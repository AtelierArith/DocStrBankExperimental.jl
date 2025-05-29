# 拡張ヘルプ

```
translate(v::AbstractVector, P::HPolygon; [share]::Bool=false)
```

### 入力

  * `share` – （オプション、デフォルト: `false`）元の集合表現の未変更部分を共有するためのフラグ

### 注意事項

制約の法線ベクトル（ベクトル `a` は `a⋅x ≤ b` の形） は、`share == true` の場合、元の制約と共有されます。

### アルゴリズム

すべての制約を翻訳します。
