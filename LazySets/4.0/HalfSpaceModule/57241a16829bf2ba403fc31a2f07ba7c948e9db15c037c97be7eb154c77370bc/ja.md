# 拡張ヘルプ

```
translate(hs::HalfSpace, v::AbstractVector; [share]::Bool=false)
```

### 注意事項

半空間の法線ベクトル（ベクトル `a` は `a⋅x ≤ b` の中で）は、`share == true` の場合に元の半空間と共有されます。

### アルゴリズム

半空間 $a⋅x ≤ b$ は、半空間 $a⋅x ≤ b + a⋅v$ に変換されます。言い換えれば、ドット積 $a⋅v$ を $b$ に加えます。
