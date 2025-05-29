```
fusenodes(fens1::FENodeSet{T}, fens2::FENodeSet{T}, tolerance::T) where {T<:Number}
```

Fuse together nodes from two node sets.

Fuse two node sets. If necessary, by gluing together nodes located within tolerance of each other. The two node sets, `fens1` and `fens2`,  are fused together by merging the nodes that fall within a box of size `tolerance`. The merged node set, `fens`, and the new  indexes of the nodes in the set `fens1` are returned.

The set `fens2` will be included unchanged, in the same order, in the node set `fens`. The indexes of the node set `fens1` will have changed.

# Example

After the call to this function we have `k=new_indexes_of_fens1_nodes[j]` is the node in the node set `fens` which used to be node `j` in node set `fens1`. The finite element set connectivity that used to refer to `fens1` needs to be updated to refer to the same nodes in  the set `fens` as      `updateconn!(fes, new_indexes_of_fens1_nodes);`
