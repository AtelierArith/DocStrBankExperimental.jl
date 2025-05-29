```
mappedcrs(x)
```

配列の `Y`/`X` 次元のマッピングされた座標参照系を取得します。

[`Projected`](@ref) ルックアップでは、これはマッピングされた座標参照系で定義された投影から基礎となる投影への [`Selector`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Selector) 値を変換し、マッピングされた投影でプロット軸を表示するために使用されます。

`Mapped` ルックアップでは、これはインデックス値の座標参照系です。手動で設定するには [`setmappedcrs`](@ref) を参照してください。
