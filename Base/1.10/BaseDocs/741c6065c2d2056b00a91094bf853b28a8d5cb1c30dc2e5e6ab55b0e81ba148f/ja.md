```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

`x.f`の`expected`から`desired`への比較とスワップ操作を行います。関数呼び出し形式の代わりに、構文`@atomic_replace! x.f expected => desired`を使用できます。

また、[`replacefield!`](@ref Core.replacefield!)および[`setproperty!`](@ref Base.setproperty!)も参照してください。
