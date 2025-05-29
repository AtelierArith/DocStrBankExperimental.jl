# 拡張ヘルプ

```
translate(H::Hyperrectangle, v::AbstractVector; [share]::Bool=false)
```

### 入力

  * `H`     – ハイパーレクタングル
  * `v`     – 変換ベクトル
  * `share` – （オプション、デフォルト: `false`）元の集合表現の未変更部分を共有するためのフラグ

### 注意事項

半径ベクトルは、`share == true` の場合、元のハイパーレクタングルと共有されます。
