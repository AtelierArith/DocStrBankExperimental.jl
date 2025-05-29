```
hungarian(costMat) -> (assignment, cost)
```

Find an optimal solution of the rectangular assignment problem represented by the $N x M$ matrix `costMat`. Return the optimal column indices and corresponding minimal cost.

The `costMat[n,m]` denotes the `cost` to assign the `n`th worker to the `m`th job. The zero element in the return value `assignment` means that these workers have no assigned job.

Elements in the matrix can be set to `missing`. In this case, the corresponding matching cannot be considered by the algorithm.

# Examples

```julia
julia> A = [ 24     1     8;
              5     7    14;
              6    13    20;
             12    19    21;
             18    25     2];

julia> assignment, cost = hungarian(A)
([2,1,0,0,3],8)

julia> assignment, cost = hungarian(A')
([2,1,5],8)

julia> using Missings

julia> costMat = [ missing  1   1
                      1     0   1
                      1     1   0 ]
3×3 Array{Union{Float64, Missings.Missing},2}:
missing  1.0  1.0
  1.0    0.0  1.0
  1.0    1.0  0.0

julia> hungarian(costMat)
([2, 1, 3], 2)
```
