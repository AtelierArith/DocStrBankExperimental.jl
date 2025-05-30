```
has_recanting_witness(g::AbstractGraph, u, v,  blocked_edges::AbstractGraph) -> Bool
```

In a causal DAG with edges `g`, determine whether path-specific causal effect from vertex `u` to `v` with edges in `blocked_edges` blocked can be can be computed uniquely from the data available to the investigator (assuming complete observations), which is the case if there is no "recanting witness". Essentially this means that `blocked_edges` could equivalently be replaced by a blocking only outgoing edges of `u`. 

See Alvin, Shpitser, Pearl (2005): "Identifiability of Path-Specific Effects",  https://ftp.cs.ucla.edu/pub/stat_ser/r321-L.pdf.    
