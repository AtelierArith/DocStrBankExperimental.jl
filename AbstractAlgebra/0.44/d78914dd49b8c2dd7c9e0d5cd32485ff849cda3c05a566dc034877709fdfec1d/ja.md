```
rand(S::MSeriesRing, term_range, v...)
```

系列環 $S$ のランダムな要素を返します。項の数は `term_range` で指定された範囲内で、系列の係数は与えられたデータ `v` を使用して基底環でランダムに生成されます。項の変数の指数は、$S$ が作成されたときの精度制限よりも小さくなります。
