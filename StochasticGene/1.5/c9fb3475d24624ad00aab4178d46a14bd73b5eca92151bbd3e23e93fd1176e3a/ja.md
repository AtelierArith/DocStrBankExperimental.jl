```
test_fit_rnadwelltime(; rtarget, transitions, G, R, S, insertstep, nRNA, nsamples, nalleles, onstates, bins, dttype, fittedparam, propcv, priorcv, splicetype, maxtime, nchains)
```

提供されたパラメータを使用してシミュレートされたRNA滞留時間ヒストグラムをフィットさせ、データと比較します。

# 引数

  * `rtarget`, `transitions`, `G`, `R`, `S`, `insertstep`: モデル構造とレート。
  * `nRNA`, `nsamples`, `nalleles`, `onstates`, `bins`, `dttype`: データとシミュレーションオプション。
  * `fittedparam`, `propcv`, `priorcv`, `splicetype`, `maxtime`, `nchains`: フィッティングオプション。

# 戻り値

  * (予測ヒストグラム, データPDF) のタプル。
