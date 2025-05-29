```
remove_periodicity!(sys::System, flags)
```

各次元 `d` に対して `flags[d]` が `true` の場合、周期的相互作用を削除します。システムは [`to_inhomogeneous`](@ref) を介して不均一な相互作用をサポートする必要があります。

# 例

```julia
# 1次元目と3次元目に沿った周期境界を削除
remove_periodicity!(sys::System, (true, false, true))
```
