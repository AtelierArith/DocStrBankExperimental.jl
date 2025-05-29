```
overapproximate(S::LazySet, ::Type{<:Interval})
```

セットの上限近似を区間で返します。

### 入力

  * `S`        – 一次元セット
  * `Interval` – 目標タイプ

### 出力

区間。

### アルゴリズム

`extrema` 関数を使用します。
