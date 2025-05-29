```
reduction_error(rs)
```

[`HRedSys`](@ref) のための削減誤差を計算します。

# 引数

完全なシステムと削減されたシステムがすでに統合されている場合、削減誤差はより迅速に計算できます：

```julia
reduction_error(rs, sol_full, sol_reduced)
```

これにより、それぞれのシステムを再度統合するコストが節約されます。
