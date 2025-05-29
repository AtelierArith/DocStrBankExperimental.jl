```
@jwait [kernelname[ accelname]]
```

デバイス操作の完了を待機します。

`kernelname` または `accelname` が指定されていない場合、現在アクティブな accel または kernel コンテキストが使用されます。

# 引数

[`@jaccel`](@jaccel)、[`@jkernel`](@jkernel)も参照してください。

# 例

```julia-repl
julia> @jwait mykernel
0
```

# 実装

T.B.D. ```
