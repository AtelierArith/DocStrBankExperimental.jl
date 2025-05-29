```
@derived_dimension(name, dims, autodocs=false)
```

派生次元の [`Unitful.Quantity`](@ref)、[`Unitful.Level`](@ref)、および [`Unitful.Units`](@ref) オブジェクトに対してディスパッチを許可するための型エイリアスを作成します。面積のような派生次元は、単に長さの二乗です。型エイリアスはエクスポートされません。`autodocs == true` の場合、これらのエイリアスのためのドキュメント文字列が自動的に生成されます。

!!! compat "Unitful 1.10"
    `autodocs` 引数は Unitful 1.10 以降が必要です。


`dims` は [`Unitful.Dimensions`](@ref) オブジェクトです。

`nothing` を返します。

使用例:

  * `@derived_dimension Area 𝐋^2` は `Area` と `AreaUnit` の型エイリアスを生成します
  * `@derived_dimension Speed 𝐋/𝐓` は `Speed` と `SpeedUnit` の型エイリアスを生成します
