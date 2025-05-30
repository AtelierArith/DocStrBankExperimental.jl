```
getrowrange(n, idx)
```

行列の行範囲を取得します。`n` 行の行列に対して、クワッドツリーからの `idx` に対応します。

# 引数

  * `n::Integer`: 行列の行数。
  * `idx::T where T<:Integer`: 行列に対応するクワッドツリーからのインデックス。

# 戻り値

`::UnitRange{Int64}`: `idx` に対応する行列の行範囲。

# 例

```@repl
using WaveletsExt

x = randn(8,8)
tree = maketree(x, 3, :full)
getrowrange(8,3)            # 1:4
```

**関連項目:** [`Wavelets.Util.maketree`](@ref), [`getcolrange`](@ref)
