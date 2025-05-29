```
nm_measurement(state, vertexset)
```

Return joint probability of cannonical measurement of density matrix `state`, according to `vertexset`.

*Note:* It is up to user to provide proper density state.

# Examples

```jldoctest; setup = :(using QSWalk)
julia> state = [1/6 0 1/6; 0 2/3 0; 1/6 0 1/6]
3×3 Array{Float64,2}:
 0.166667  0.0       0.166667
 0.0       0.666667  0.0
 0.166667  0.0       0.166667

julia> nm_measurement(state, VertexSet([[1, 3], [2]]))
2-element Array{Float64,1}:
 0.3333333333333333
 0.6666666666666666
```
