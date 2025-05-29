スタックを吹き飛ばさない末尾再帰。

```
@bounce even(n) = n == 0 ? true : odd(n-1)
@bounce odd(n) = n == 0 ? false : even(n-1)

even(1_000_000) # `@bounce`なしではスタックが吹き飛びます。
#> true
```

単純なケースでは、おそらくはるかに速い [`@rec`](@ref) を使用したいでしょう。
