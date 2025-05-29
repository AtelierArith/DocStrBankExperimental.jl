```
test_fit_tracejoint(; coupling, G, R, S, insertstep, transitions, rtarget, rinit, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, maxtime, method)
```

結合モデルのためのシミュレーションされたジョイントトレースデータセットをフィットし、ターゲットと比較します。

# 引数

  * `coupling`, `G`, `R`, `S`, `insertstep`, `transitions`: モデル構造と結合。
  * `rtarget`, `rinit`: レートパラメータ。
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: データとシミュレーションオプション。
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `maxtime`, `method`: フィッティングオプション。

# 戻り値

  * (フィットしたレート, ターゲットレート) のタプル。
