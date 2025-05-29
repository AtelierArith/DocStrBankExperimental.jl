```
ITensor([ElT::Type, ]::AbstractArray, inds; tol=0.0, checkflux=true)
```

Create a block sparse ITensor from the input Array, and collection of QN indices. Zeros are dropped and nonzero blocks are determined from the zero values of the array.

Optionally, you can set a tolerance such that elements less than or equal to the tolerance are dropped.

By default, this will check that the flux of the nonzero blocks are consistent with each other. You can disable this check by setting `checkflux=false`.

# Examples

```julia
julia> i = Index([QN(0)=>1, QN(1)=>2], "i");

julia> A = [1e-9 0.0 0.0;
            0.0 2.0 3.0;
            0.0 1e-10 4.0];

julia> @show ITensor(A, i', dag(i); tol = 1e-8);
ITensor(A, i', dag(i); tol = 1.0e-8) = ITensor ord=2
Dim 1: (dim=3|id=468|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=468|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{Float64,Array{Float64,1},2}
 3×3
Block: (2, 2)
 [2:3, 2:3]
 2.0  3.0
 0.0  4.0
```
