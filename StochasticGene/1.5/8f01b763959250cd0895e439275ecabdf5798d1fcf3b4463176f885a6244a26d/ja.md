```
test_fit_rna(; gene, G, nalleles, propcv, fittedparam, fixedeffects, transitions, rinit, datacond, datapath, label, root, nchains)
```

提供されたパラメータを使用して実際のRNAヒストグラムをフィットし、データと比較します。

# 引数

  * `gene`, `G`, `nalleles`: 遺伝子とモデル構造。
  * `propcv`, `fittedparam`, `fixedeffects`, `transitions`, `rinit`: フィッティングオプション。
  * `datacond`, `datapath`, `label`, `root`: データとファイルオプション。
  * `nchains`: MCMCチェーンの数。

# 戻り値

  * (予測ヒストグラム、正規化データヒストグラム) のタプル。
