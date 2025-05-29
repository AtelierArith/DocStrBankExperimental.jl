```
getdepth(idx, tree_type)
```

`idx`の深さを二分木または四分木で取得します。

# 引数

  * `idx::T where T<:Integer`: ノードのインデックス。
  * `tree_type::Symbol`: 木のタイプ。サポートされているタイプは `:binary` と `:quad` の木です。

# 戻り値

`::T`: ノード `idx` の深さ。

# 例

```@repl
using WaveletsExt

getdepth(1,:binary)     # 0
getdepth(3,:binary)     # 1
getdepth(8,:binary)     # 3

getdepth(1,:quad)       # 0
getdepth(3,:quad)       # 1
getdepth(8,:quad)       # 2
```

**参照:** [`Wavelets.Util.maketree`](@ref)
