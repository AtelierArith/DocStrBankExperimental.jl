```
corners = imcorner(img; [method])
corners = imcorner(img, threshold; [method])
```

コーナー検出を次のいずれかの方法を使用して実行します -

```
1. harris
2. shi_tomasi
3. kitchen_rosenfeld
```

各メソッドのパラメータは、そのドキュメントに記載されています。結果の応答の最大値がコーナーとして取得されます。しきい値が指定されている場合、応答の値はしきい値処理されてコーナーピクセルが得られます。`threshold`が`Percentile`の場合、その型は保持されます。
