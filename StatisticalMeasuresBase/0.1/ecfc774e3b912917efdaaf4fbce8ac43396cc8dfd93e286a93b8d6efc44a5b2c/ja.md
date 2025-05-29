```
robust_measure(measure)
```

新しい測定値 `robust` を返します：

  * `weights` と `class_weights` は、`measure` によってサポートされていない場合、静かに均一（単位）として扱われます
  * `weights` または `class_weights` のいずれかが `nothing` の場合、引数が省略されたかのように扱われます（均一として解釈されます）

これは、すべての呼び出し `robust(ŷ, y, weights, class_weights)` または `measurements(robust, ŷ, y, weights, class_weights)` の形式に対して成り立ち、それ以外の場合の `robust` の動作は `measure` と同じです。
