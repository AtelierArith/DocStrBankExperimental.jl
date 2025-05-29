```
scanmle(data; ntrials=100, stderrcutoff=0.1, useKS=false)
```

`data`に対して約`ntrials`回`mle`を実行し、`xmin`を増加させます。推定値`alpha`の標準誤差が`stderrcutoff`を超えた場合、試行を停止します。`useKS`がtrueの場合、最小のKS統計量を与える`mle`の適用が返されます。スキャンの統計を含むオブジェクトを返します。

`scanmle`はデータの尾のパワー法則の挙動を分析することを目的としています。
