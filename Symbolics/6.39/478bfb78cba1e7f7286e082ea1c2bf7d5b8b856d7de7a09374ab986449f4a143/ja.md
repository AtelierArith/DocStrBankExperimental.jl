```
rootfunction(f)
```

不連続点または不連続導関数を持つ関数 `f` が与えられたとき、`f` の根を求める関数を返します。根を求める関数 `g` は `f` と同じ引数を取り、`f` は `g` の符号に基づいて区分的に定義され、各区間は連続であり、連続導関数を持つことができます。区間は `left_continuous_function(f)` と `right_continuous_function(f)` を使用して取得されます。

より正式には、

```julia
f(args...) = if g(args...) < 0
    left_continuous_function(f)(args...)
else
    right_continuous_function(f)(args...)
end
```

例えば、`f` が `max(x, y)` の場合、根関数は `(x, y) -> x - y` であり、`left_continuous_function` は `(x, y) -> y`、`right_continuous_function` は `(x, y) -> x` です。

参照: [`left_continuous_function`](@ref), [`right_continuous_function`](@ref).
