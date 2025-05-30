```
add!!(x, t::InplacableThunk)
```

[`InplaceableThunk`](@ref) に対する `add!!` の特化は、`x` が適切に可変である場合にのみ `t.add!` を `x` に対して呼び出すことを約束します。そうでない場合は、場所を外れた操作になります。
