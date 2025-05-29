```
line_graph(G::AbstractGraph;
           vertex_labels::Array{Symbol, 1}=Symbol[])
```

Return a LabeledGraph representing the line graph of the 'G'. 

The label for each each vertex of the line graph is created by  concatenating the labels of the corresponding vertices in 'G'.

The symbols in the array `vertex_labels` are used as labels for the vertices of the returned line graph. If `vertex_labels` is empty then labels are created by combining the indices of  the corresponding vertices in 'G'.
