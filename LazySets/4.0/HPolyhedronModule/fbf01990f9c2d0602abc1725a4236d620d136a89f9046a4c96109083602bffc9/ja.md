# 拡張ヘルプ

```
translate(P::HPoly, v::AbstractVector; [share]::Bool=false)
```

### 入力

  * `share` – （オプション、デフォルト: `false`）元の集合表現の未変更部分を共有するためのフラグ

### 注意事項

制約の法線ベクトル（ベクトル `a` は `a⋅x ≤ b` における） は、`share == true` の場合、元の制約と共有されます。
