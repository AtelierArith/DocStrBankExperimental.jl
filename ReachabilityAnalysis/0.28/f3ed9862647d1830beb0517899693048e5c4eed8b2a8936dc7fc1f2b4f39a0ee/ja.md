```
normalize(ivp::InitialValueProblem)
```

初期値問題を正規化（または標準）形式に変換します。

### 入力

  * `ivp` – 初期値問題

### 出力

すでに標準形式に適合している場合は同じ初期値問題、そうでない場合は新しいもの。

### 注意事項

この関数は初期値問題のための [`normalize`](@ref normalize(::AbstractSystem)) を拡張します。
