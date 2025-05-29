```
ffindnz(arr)
```

`arr`の非ゼロ要素を返します。`arr`をFinchが理解するように返します。返されるのは`(I..., V)`で、ここで`I`は`arr`の各モードに対する座標ベクトルであり、`V`は対応する非ゼロ値のベクトルで、[`fsparse`](@ref)に渡すことができます。

関連情報: (`findnz`)(https://docs.julialang.org/en/v1/stdlib/SparseArrays/#SparseArrays.findnz)
