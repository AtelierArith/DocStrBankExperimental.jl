```
corners = imcorner(img; [method])
corners = imcorner(img, threshold; [method])
```

コーナー検出を次のいずれかの方法を使用して実行します -     1. harris     2. shi*tomasi     3. kitchen*rosenfeld 各メソッドのパラメータはそのドキュメントに記載されています。結果の応答の最大値がコーナーとして取得されます。しきい値が指定されている場合、応答の値はコーナーピクセルを得るためにしきい値処理されます。`threshold`が`Percentile`の場合、その型は保持されます。
