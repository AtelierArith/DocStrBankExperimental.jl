```
test_fit_trace(; G, R, S, insertstep, transitions, rtarget, rinit, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, nchains)
```

シミュレーションされたトレースデータセットを提供されたパラメータを使用してフィットし、ターゲットと比較します。

# 引数

  * `G`, `R`, `S`, `insertstep`, `transitions`: モデル構造。
  * `rtarget`, `rinit`: レートパラメータ。
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: データおよびシミュレーションオプション。
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `nchains`: フィッティングオプション。

# 戻り値

  * (フィットしたレート, ターゲットレート) のタプル。
