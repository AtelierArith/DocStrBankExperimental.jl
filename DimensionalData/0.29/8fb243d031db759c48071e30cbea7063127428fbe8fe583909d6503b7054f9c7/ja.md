```
DimIndices <: AbstractArray

DimIndices(x)
DimIndices(dims::Tuple)
DimIndices(dims::Dimension)
```

`Dimension`のための`CartesianIndices`のようなもの。`dims`の軸インデックスのすべての組み合わせに対して、`Dimension(i)`の`Tuple`の`Array`として振る舞います。

これは、配列の任意の次元を表示/インデックスするために使用でき、特に`otherdims`と組み合わせると、未知の次元のインデックスを反復処理するのに便利です。

`DimIndices`は、`CartesianIndices`のように`getindex`で直接使用でき、個々の`Dimension`や`Dimension`のタプルと自由に混ぜることができます。

## 例

`DimArray`を`DimIndices`でインデックスします。

`CartesianIndices`とは異なり、次元の順序が同じでない場合でも問題ありません。あるいは、すべてが含まれていなくても問題ありません。

```jldoctest; setup = :(using DimensionalData, Random; Random.seed!(123))
julia> A = rand(Y(0.0:0.3:1.0), X('a':'f'))
┌ 4×6 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────── dims ┐
  ↓ Y Sampled{Float64} 0.0:0.3:0.9 ForwardOrdered Regular Points,
  → X Categorical{Char} 'a':1:'f' ForwardOrdered
└─────────────────────────────────────────────────────────────────┘
 ↓ →   'a'       'b'       'c'        'd'        'e'       'f'
 0.0  0.9063    0.253849  0.0991336  0.0320967  0.774092  0.893537
 0.3  0.443494  0.334152  0.125287   0.350546   0.183555  0.354868
 0.6  0.745673  0.427328  0.692209   0.930332   0.297023  0.131798
 0.9  0.512083  0.867547  0.136551   0.959434   0.150155  0.941133

julia> di = DimIndices((X(1:2:4), Y(1:2:4)))
┌ 2×2 DimIndices{Tuple{X{Int64}, Y{Int64}}, 2} ┐
├──────────────────────────────────────── dims ┤
  ↓ X 1:2:3,
  → Y 1:2:3
└──────────────────────────────────────────────┘
 ↓ →  1                3
 1     (↓ X 1, → Y 1)   (↓ X 1, → Y 3)
 3     (↓ X 3, → Y 1)   (↓ X 3, → Y 3)

julia> A[di] # これらのインデックスでAをインデックスします
┌ 2×2 DimArray{Float64, 2} ┐
├──────────────────────────┴──────────────────────────────── dims ┐
  ↓ Y Sampled{Float64} 0.0:0.6:0.6 ForwardOrdered Regular Points,
  → X Categorical{Char} 'a':2:'c' ForwardOrdered
└─────────────────────────────────────────────────────────────────┘
 ↓ →   'a'       'c'
 0.0  0.9063    0.0991336
 0.6  0.745673  0.692209
```
