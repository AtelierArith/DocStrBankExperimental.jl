```
colorview(C)
```

`(As...) -> colorview(C, Ax...)` と同等の関数を作成します。

# 例

```jldoctest; setup = :(using ImageCore)
julia> ones(Float32, 2, 2) |> colorview(Gray)
2×2 reinterpret(reshape, Gray{Float32}, ::Matrix{Float32}) with eltype Gray{Float32}:
 Gray{Float32}(1.0)  Gray{Float32}(1.0)
 Gray{Float32}(1.0)  Gray{Float32}(1.0)
```

これは、例えばチャネルデータのバッチを変換したいときに少し便利です：

```julia
julia> Rs, Gs, Bs = ntuple( i -> [randn(2, 2) for _ in 1:4], 3)

julia> map(colorview(RGB), Rs, Gs, Bs)
```
