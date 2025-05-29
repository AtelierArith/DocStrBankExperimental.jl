```
quadpoints(refspace, charts, rules)
```

重み、点、値の三重項を含むベクトルの行列を計算し、チャートによって記述された要素上での数値積分に使用できます。内部的に、このメソッドは `quadpoints(chart, rule)` を使用して、特定の数値積分ルールに対する点と重みを `chart` の上で取得します。
