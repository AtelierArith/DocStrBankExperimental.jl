```
parallel(mm1::MeasurementModel, models::MeasurementModel...)
```

同じ入力で動作する `MeasurementModel` を組み合わせて、すべての測定モデルの出力の組み合わせを生成するメカニズムを実装します。これは、計算が2つ以上の異なる計算に分岐し、後で合成される場合に便利です。例に示すように。

例:

```
j = parallel(f,g) # ParallelMeasurementModel([f,g], true) を作成
y = j(x) # ここで y は f(x) と h(x) の出力を組み合わせる
z = parallel(f, g, h)(x) # 概念的には combine(f(x), g(x), h(x)) を単一の出力にする
(k ∘ parallel(f, g, h))(x) == k(z) # 概念的には k(f(x),g(x),h(x)) のようなもの
```
