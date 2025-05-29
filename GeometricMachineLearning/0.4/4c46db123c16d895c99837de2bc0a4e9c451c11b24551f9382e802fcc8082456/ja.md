```
projection_error(rs)
```

[`HRedSys`](@ref) の射影誤差を計算します。

# 引数

完全なシステムがすでに統合されている場合、射影誤差はより迅速に計算できます：

```julia
projection_error(rs, sol_full)
```

これにより、システムを再度統合するコストが節約されます。
