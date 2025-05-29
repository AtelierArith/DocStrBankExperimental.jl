```
zerovector(x, [S::Type{<:Number} = scalartype(x)])
```

`x`のベクトル空間におけるゼロベクトルを返します。オプションで、結果のゼロベクトルのために修正されたスカラー型`S`を指定できます。

!!! note
    新しい型は、該当する場合、2引数バージョンのみを実装するべきです。


また参照: [`zerovector!`](@ref), [`zerovector!!`](@ref)
