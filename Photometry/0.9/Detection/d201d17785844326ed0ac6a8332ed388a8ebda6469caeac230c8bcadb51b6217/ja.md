```
PeakMesh(box_size=(3, 3), nsigma=3.0)
```

画像全体のグリッドでしきい値を超えるピークを見つけることによってソースを検出します。

これは、[`extract_sources`](@ref)と一緒に使用する際に`error * nsigma`を計算することによって、ソースのためのピクセル単位のしきい値を作成します。ピークは、`box_size`のサイズのボックスで画像を検索することによって見つけられます。そのボックス内の最大値が上記で設定されたしきい値を超えている場合、その点が抽出されます。
