```
ArrayAxes{N}
```

は、基本メソッド `axes(A::AbstractArray)` によって返される配列軸の標準的な型です。これは [`ArrayAxis`](@ref) インスタンスの `N`-タプルです。引数を配列軸に変換するために、メソッド [`as_array_axes`](@ref) を呼び出すことができます。

関連情報としては、[`ArrayShape`](@ref)、`Dims` があります。
