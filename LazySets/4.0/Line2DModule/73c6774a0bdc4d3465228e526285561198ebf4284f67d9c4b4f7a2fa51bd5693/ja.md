# 拡張ヘルプ

```
translate(L::Line2D, v::AbstractVector; [share]::Bool=false)
```

### 注意事項

線の法線ベクトル（ベクトル `a` は `a⋅x = b` の形） は、`share == true` の場合に元の線と共有されます。

### アルゴリズム

線 $a⋅x = b$ は、線 $a⋅x = b + a⋅v$ に変換されます。言い換えれば、ドット積 $a⋅v$ を $b$ に加えます。
