```
c = coord(node)
```

Used by element constructors to obtain the coordinates of a vector of Nodes handed by Muscade to the constructor. `c` is accessed as 

```
c[inod][icoord]
```

where `inod` is the element-node number and `icoord` an index into a vector of coordinates.

Note that `c[inod]` points at the same memory as `nod[inod].coord`: do not mutate `c[inod]`!

See also: [`addnode!`](@ref), [`addelement!`](@ref), [`describe`](@ref), [`solve`](@ref)  
