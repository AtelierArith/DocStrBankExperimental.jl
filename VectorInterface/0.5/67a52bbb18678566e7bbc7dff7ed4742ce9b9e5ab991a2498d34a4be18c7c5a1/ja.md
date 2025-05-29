```
zerovector!!(x, [S::Type{<:Number} = scalartype(x)])
```

ベクトル空間 `x` におけるゼロベクトルを構築し、可能であれば `x` を上書きして再利用しようとします。オプションとして、結果のゼロベクトルのために修正されたスカラー型 `S` を指定できます。

!!! note
    新しい型は一引数バージョンのみを実装するべきです。二引数バージョンは `S == scalartype(x) ? zerovector!!(x) : zerovector(x, S)` に相当します。


また、[`zerovector`](@ref) や [`zerovector!`](@ref) も参照してください。
