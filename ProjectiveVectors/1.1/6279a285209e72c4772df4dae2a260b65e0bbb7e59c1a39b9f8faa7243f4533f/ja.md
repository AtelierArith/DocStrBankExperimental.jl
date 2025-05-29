```
affine_chart(z::PVector)
```

プロジェクティブベクトルに対応するアフィンチャートを返します。これは[`embed`](@ref)の逆と見なすことができます。

## 例

```julia-repl
julia> v = embed([2.0, 3, 4, 5, 6, 7], (2, 3, 1))
PVector{Float64, 3}:
 [2.0, 3.0, 1.0] × [4.0, 5.0, 6.0, 1.0] × [7.0, 1.0]

julia> affine_chart(v)
6-element Array{Float64,1}:
 2.0
 3.0
 4.0
 5.0
 6.0
 7.0
```
