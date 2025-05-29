```
read_from_gfa(filename::String; weight_file::String)
```

Read graph from GFA file and optional weight_file (contains two column `node` and `weight`) and return `GFAResult` struct which  has `g` - the graph, `w` - weight array, `l` - node label array, `e` - edge label array and `p` - path array.
