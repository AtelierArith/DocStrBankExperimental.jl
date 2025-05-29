```
direction(L::Line)
```

線の方向を返します。

### 入力

  * `L` – 線

### 出力

線の方向。

### 注意事項

方向は必ずしも正規化されているわけではありません。 [`normalize(::Line, ::Real)`](@ref) / [`normalize!(::Line, ::Real)`](@ref) を参照してください。
