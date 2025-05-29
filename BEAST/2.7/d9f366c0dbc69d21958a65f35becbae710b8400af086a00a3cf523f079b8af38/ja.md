```
quadrule(operator, test_refspace, trial_refspace, test_index, test_chart, trial_index, trial_chart, quad_data)
```

オペレータカーネルとテストおよびトライアル要素に基づいて、この関数は、相互作用積分を正確に計算するために使用する必要がある数値積分ルールを指定する型とデータフィールドを持つオブジェクトを構築します。`quaddata`によって作成された`quad_data`オブジェクトは、数値積分点や重み、幾何学的量などの事前計算されたデータの再利用を可能にするために渡されます。

返される数値積分ルールの型は、`momintegrals`のどのメソッドをディスパッチするかを決定するのに役立ちます。
