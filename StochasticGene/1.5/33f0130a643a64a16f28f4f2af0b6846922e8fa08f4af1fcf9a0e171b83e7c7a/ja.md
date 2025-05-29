```
test_fit_rnaonoff(; G, R, S, transitions, insertstep, rtarget, rinit, nsamples, nhist, nalleles, onstates, bins, fittedparam, propcv, priorcv, splicetype, nchains)
```

提供されたパラメータを使用してシミュレートされたRNAオンオフヒストグラムをフィットさせ、データと比較します。

# 引数

  * `G`, `R`, `S`, `transitions`, `insertstep`: モデル構造。
  * `rtarget`, `rinit`: レートパラメータ。
  * `nsamples`, `nhist`, `nalleles`, `onstates`, `bins`: データおよびシミュレーションオプション。
  * `fittedparam`, `propcv`, `priorcv`, `splicetype`, `nchains`: フィッティングオプション。

# 戻り値

  * (予測ヒストグラム, データPDF)のタプル。
