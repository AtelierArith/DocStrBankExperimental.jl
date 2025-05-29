```
brownians_in_use(itos::Array{ItoIntegral,1}, brownians::Array{Symbol,1})
```

配列の `ItoIntegral` に使用されているブラウン運動を特定します。

### 入力

  * itos - 各イート積分を含む辞書
  * brownians - すべての可能なブラウン運動

### 出力

  * itos に使用されているブラウン運動の `Vector`
  * これらのブラウン運動のインデックスを持つ `Vector`。
