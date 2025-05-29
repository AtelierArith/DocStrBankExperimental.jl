```
embed(xs::AbstractVector...; normalize=false)
embed(x::AbstractVector{T}, dims::NTuple{N, Int}; normalize=false)::PVector{T, N}
```

アフィンベクトル `x` を、`dims` に従って `x` の各部分集合 `xᵢ` に対してマップ πᵢ: xᵢ -> [xᵢ; 1] によってアフィン空間の積に埋め込みます。`normalize` が true の場合、ベクトルは正規化されます。

## 例

```julia-repl
julia> embed([2, 3])
PVector{Int64, 1}:
 [2, 3, 1]

julia> embed([2, 3], [4, 5, 6])
PVector{Int64, 2}:
 [2, 3, 1] × [4, 5, 6, 1]

julia> embed([2.0, 3, 4, 5, 6, 7], (2, 3, 1))
PVector{Float64, 3}:
 [2.0, 3.0, 1.0] × [4.0, 5.0, 6.0, 1.0] × [7.0, 1.0]

 julia> embed([2.0, 3, 4, 5, 6, 7], (2, 3, 1), normalize=true)
 PVector{Float64, 3}:
  [0.5345224838248488, 0.8017837257372732, 0.2672612419124244] × [0.45291081365783825, 0.5661385170722978, 0.6793662204867574, 0.11322770341445956] × [0.9899494936611666, 0.1414213562373095]
```
