```
tearing(sys; simplify=false)
```

システム内の非線形方程式を切り離します。`simplify=true` の場合、切り離し後の新しい残差方程式を簡略化します。エンドユーザーは、代わりにこの関数を内部で呼び出す [`structural_simplify`](@ref) を呼び出すことを推奨します。
