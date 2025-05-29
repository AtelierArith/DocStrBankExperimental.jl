```
getcolrange(n, idx)
```

`idx`に対応する`n`列の行列から列の範囲を取得します。

# 引数

  * `n::Integer`: 行列の列数。
  * `idx::T where T<:Integer`: 行列に対応するクワッドツリーからのインデックス。

# 戻り値

`::UnitRange{Int64}`: `idx`に対応する行列の列の範囲。

# 例

```@repl
using WaveletsExt

x = randn(8,8)
tree = maketree(x, 3, :full)
getcolrange(8,3)            # 5:8
```

**関連項目:** [`Wavelets.Util.maketree`](@ref), [`getrowrange`](@ref)
