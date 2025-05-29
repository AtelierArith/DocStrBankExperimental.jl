```
Directed(g_dst)
```

単方向出力関数 `g_dst` をラップし、双方向出力関数に変換します。これは次のように適用されます。

```
y_dst = g_dst(...)
```

`Directed` を使用すると、`src` 側の出力はありません。`g_dst` は、対応する [`StateMask`](@ref) を暗黙的にラップするために `Number`/`AbstractArray` であることができます。

他に [`AntiSymmetric`](@ref)、[`Symmetric`](@ref)、[`Fiducial`](@ref)、および [`StateMask`](@ref) も参照してください。
