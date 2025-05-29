```
get_GES_linelist()
```

Gaia-ESO調査のリストは[Heiter et al. 2021](https://ui.adsabs.harvard.edu/abs/2021A&A...645A.106H/abstract)からのものです。このリストには1500万以上のラインが含まれており、スペクトルを合成するのに時間がかかる場合があります。分子ラインが必要ない場合は、`include_molecules=false`を設定して処理を速くすることができます。

# キーワード引数

  * `include_molecules`（デフォルト: `true`）：分子ラインを含めるかどうか。
