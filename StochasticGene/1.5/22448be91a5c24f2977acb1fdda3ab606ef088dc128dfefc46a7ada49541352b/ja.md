```
test_fit_tracejoint_hierarchical(; coupling, G, R, S, insertstep, transitions, rtarget, rinit, hierarchical, method, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, maxtime, decayrate)
```

結合モデルのためのシミュレーションされたジョイントトレースデータセットを階層モデルを使用してフィットし、ターゲットと比較します。

# 引数

  * `coupling`, `G`, `R`, `S`, `insertstep`, `transitions`: モデル構造と結合。
  * `rtarget`, `rinit`: レートパラメータ。
  * `hierarchical`, `method`: 階層モデルとメソッドオプション。
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: データとシミュレーションオプション。
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `maxtime`, `decayrate`: フィッティングオプション。

# 戻り値

  * (フィットしたレート、ターゲットレート、フィット、統計、測定、モデル、データ、オプション) のタプル。
