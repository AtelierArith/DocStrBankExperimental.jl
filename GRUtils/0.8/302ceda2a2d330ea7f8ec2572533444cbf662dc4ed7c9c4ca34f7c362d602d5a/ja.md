```
geometrykinds([p])
```

与えられたプロットまたは図 `p` に含まれる幾何学の種類を表すシンボルのリストを返します。

引数が指定されていない場合、現在の図の現在のプロットを取得します。

# 例

```julia
julia> # 値 `(x, y)` で点のセットをプロット
julia> # `(x, ŷ)` を通る回帰直線をプロット
julia> scatter(x, y)
julia> plot(x, ŷ)
julia> geometrykinds()
2-element Array{Symbol,1}:
 :scatter
 :line
```
