# Google Sheets 

- Developed a feature-rich spreadsheet app with robust functionality for <b>cell editing, styling, and formula evaluation. </b>
- Implemented styling options, including bold, italic, underline, font customization, and cell alignment.
- Enabled formula evaluation with automatic updates for dependent cells upon changes.
- Developed formula parsing with infix to postfix conversion and postfix evaluation, including <b>DFS cycle detection.</b>
- Supported the creation and management of multiple sheets for efficient data organization.
- employed CSS techniques, <b>such as Flexbox.</b>
- Provided the ability to convert sheets to JSON format and read from JSON for data storage.
- Demonstrated a strong understanding of HTML, CSS, and Vanilla JavaScript, showcasing proficiency in state
management, optimization, and advanced spreadsheet features.

## DFS cycle detection

```cpp

class Solution{
	public:
//Function to return list containing vertices in Topological order. 
	vector<int> topoSort(int V, vector<int> adj[]) 
	{
	    // create inDgree Array/Vector for storing the inDgree 
	    vector<int> inDegree(V);
	    
	    // store the all inDgree into the array
	    for(int i = 0; i<V; i++){
	        for(auto it : adj[i]){
	            inDegree[it]++;
	        }
	    }
	    
	    queue<int> QueueDSA;
	    
	    for(int node = 0; node < V; node++){
	        if(inDegree[node] == 0){
	            QueueDSA.push(node);
	        }
	    }
	    
	    vector<int> resultArray;
	    while(!QueueDSA.empty()){
	        int node = QueueDSA.front(); QueueDSA.pop();
	        
	        resultArray.push_back(node);
	        for(auto it : adj[node]){
	            // reduce the indegree,push into the queue Those have indegree Zero
	             inDegree[it]--;
	             if(inDegree[it] == 0){
	                 QueueDSA.push(it);
	             }
	        }
	    }
	   return resultArray; 
	}
};

- Expected Time Complexity: O(V + E)
- Expected Auxiliary Space: O(V)
```