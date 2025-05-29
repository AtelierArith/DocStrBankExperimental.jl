```
ITensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds)
ITensor([::Type{ElT} = Float64, ][flux::QN = QN(), ]inds::Index...)
```

`flux` によって決定される非ゼロブロックで埋められた `zero(ElT)` の BlockSparse ストレージを持つ ITensor を構築します。

`ElT` が指定されていない場合、デフォルトは `Float64` です。

`flux` が指定されていない場合、ITensor は空になります（ブロックを含まず、フラックスは未定義になります）。フラックスは、設定された最初の要素によって設定されます。

# 例

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

未定義のフラックスでの構築:

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
