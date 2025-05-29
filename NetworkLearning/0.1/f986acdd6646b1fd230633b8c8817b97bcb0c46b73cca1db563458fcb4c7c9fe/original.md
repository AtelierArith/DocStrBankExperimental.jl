```
update_adjacency!(a,f_update)
```

Function that updates the data of an adjacency object. `a` has to be a `MatrixAdjacency` or  `GraphAdjacency` while `f_update` has to of the form `f_update = x->update_function!(x)`.

# Examples

julia> using NetworkLearning, LightGraphs

julia> A = [0 1 0; 1 0 0; 0 0 0];

julia> Am = adjacency(A) Matrix adjacency, 3 obs

julia> update*function!(X,x,y) = begin          X[x,y] += 1          X[y,x] += 1          return X        end update*function! (generic function with 2 methods)

julia> f*update(x,y) = X->update*function!(X,x,y) f_update (generic function with 1 method)

julia> for i in 1:3          update*adjacency!(Am, f*update(1,3)) # call function three times        end

julia> adjacency_matrix(Am) 3×3 Array{Int64,2}:  0  1  3  1  0  0  3  0  0
