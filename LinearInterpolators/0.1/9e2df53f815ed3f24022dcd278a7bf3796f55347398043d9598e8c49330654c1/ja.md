```
TwoDimensionalTransformInterpolator(rows, cols, ker1, ker2, R)
```

は、サイズ `cols` の入力を補間してサイズ `rows` の出力を生成する線形マッピングを提供します。これは、各次元に沿ってカーネル `ker1` と `ker2` を使用した2次元補間と、`R` によって指定されたアフィン座標変換を適用します。

ショートカットとして:

```
TwoDimensionalTransformInterpolator(rows, cols, ker, R)
```

は、`TwoDimensionalTransformInterpolator(rows,cols,ker,ker,R)` と同等であり、すべての次元に沿って同じカーネルが使用されます。
