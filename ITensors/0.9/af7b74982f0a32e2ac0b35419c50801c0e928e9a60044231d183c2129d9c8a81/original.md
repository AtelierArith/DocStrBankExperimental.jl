```
ITensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds)
ITensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds::Index...)
```

Construct an ITensor with BlockSparse storage filled with `zero(ElT)` where the nonzero blocks are determined by `flux`.

If `ElT` is not specified it defaults to `Float64`.

If `flux` is not specified, the ITensor will be empty (it will contain no blocks, and have an undefined flux). The flux will be set by the first element that is set.

# Examples

```julia
julia> i
(dim=3|id=212|"i") <Out>
 1: QN(0) => 1
 2: QN(1) => 2

julia> @show ITensor(QN(0), i', dag(i));
ITensor(QN(0), i', dag(i)) = ITensor ord=2
Dim 1: (dim=3|id=212|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=212|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{Float64, Vector{Float64}, 2}
 3×3
Block(1, 1)
 [1:1, 1:1]
 0.0

Block(2, 2)
 [2:3, 2:3]
 0.0  0.0
 0.0  0.0

julia> @show ITensor(QN(1), i', dag(i));
ITensor(QN(1), i', dag(i)) = ITensor ord=2
Dim 1: (dim=3|id=212|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=212|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{Float64, Vector{Float64}, 2}
 3×3
Block(2, 1)
 [2:3, 1:1]
 0.0
 0.0

julia> @show ITensor(ComplexF64, QN(1), i', dag(i));
ITensor(ComplexF64, QN(1), i', dag(i)) = ITensor ord=2
Dim 1: (dim=3|id=212|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=212|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{ComplexF64, Vector{ComplexF64}, 2}
 3×3
Block(2, 1)
 [2:3, 1:1]
 0.0 + 0.0im
 0.0 + 0.0im

julia> @show ITensor(undef, QN(1), i', dag(i));
ITensor(undef, QN(1), i', dag(i)) = ITensor ord=2
Dim 1: (dim=3|id=212|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=212|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{Float64, Vector{Float64}, 2}
 3×3
Block(2, 1)
 [2:3, 1:1]
 0.0
 1.63e-322
```

Construction with undefined flux:

```julia
julia> A = ITensor(i', dag(i));

julia> @show A;
A = ITensor ord=2
Dim 1: (dim=3|id=212|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=212|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.EmptyStorage{NDTensors.EmptyNumber, NDTensors.BlockSparse{NDTensors.EmptyNumber, Vector{NDTensors.EmptyNumber}, 2}}
 3×3



julia> isnothing(flux(A))
true

julia> A[i' => 1, i => 2] = 2
2

julia> @show A;
A = ITensor ord=2
Dim 1: (dim=3|id=212|"i")' <Out>
 1: QN(0) => 1
 2: QN(1) => 2
Dim 2: (dim=3|id=212|"i") <In>
 1: QN(0) => 1
 2: QN(1) => 2
NDTensors.BlockSparse{Int64, Vector{Int64}, 2}
 3×3
Block(1, 2)
 [1:1, 2:3]
 2  0

julia> flux(A)
QN(-1)
```
