```
Fiducial(g_src, g_dst)
```

二つの片側出力関数 `g_src` と `g_dst` をラップし、次のように適用される両側出力関数に変換します。

```
y_dst = g_src(...)
y_src = g_dst(...)
```

`g` は `Number`/`AbstractArray` であり、対応する [`StateMask`](@ref) を暗黙的にラップします。

他に [`AntiSymmetric`](@ref)、[`Directed`](@ref)、[`Fiducial`](@ref) および [`StateMask`](@ref) も参照してください。
