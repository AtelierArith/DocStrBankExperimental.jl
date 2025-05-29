```
Symmetric(g)
```

単側出力関数 `g` をラップし、二重側出力関数に変換します。これは次のように適用されます。

```
y_dst = g(...)
y_src = y_dst
```

`g` は `Number`/`AbstractArray` であり、対応する [`StateMask`](@ref) を暗黙的にラップします。

他に [`AntiSymmetric`](@ref)、[`Directed`](@ref)、[`Fiducial`](@ref)、および [`StateMask`](@ref) も参照してください。
