```
detectorresponse(det::EDSDetector, eff::DetectorEfficiency, incidence::Float64=π/2)::AbstractMatrix
```

検出器の応答をモデル化する行列を構築します。これには、検出器の効率、解像度、エスケープピークなどの側面が含まれます。線形モデル内でモデル化できるすべての欠点を含みますが、非線形のコインシデンスピークのようなものは含まれません。この関数は、より多くの欠点を含むより洗練された検出器モデルのために特化されることができます（すべきです！）。

また、入力エネルギーを `EDSDetector` と同じスケールで離散化します（したがって、正方形です）。これは、検出器チャネル幅が解像度よりもはるかに小さい場合には合理的です。

例：

```
genint = computegeneratedintensity(....) # 特徴的またはブレムストラールング...
det = simpleEDS(4096, 5.0, 0.0, 132.0, 10)
eff = SDDEfficiency(AP33Tabulation(); thickness=0.0370, deadlayer=30.0e-7, entrance=Film(pure(n"Al"), 10.0e-7))
resp = detectorresponse(det, eff)
# 最後に測定された信号を計算します
measured = resp*genint
```
