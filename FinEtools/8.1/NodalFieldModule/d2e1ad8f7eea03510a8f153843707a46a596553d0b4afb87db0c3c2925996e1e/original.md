```
NodalField(data::Vector{T}) where {T<:Number}
```

Constructor of nodal field. The values of the field are given by the vector on input, `data`. This vector needs to have as many entries as there are nodes; there is just one degree of freedom per node.
