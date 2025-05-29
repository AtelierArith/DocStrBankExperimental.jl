```
poset_builder(objects::Vector{T}, comp_func::Function)::Poset where {T}
```

Given a list of `objects` and a function `comp_func` for comparing functions,  create a `Poset` in which object `i` is less than object `j` provided  `comp_func(objects[i], objects[j])` returns `true`. 

Throws an error if a cycle is created. 
