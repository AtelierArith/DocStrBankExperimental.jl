```
test_fit_trace_hierarchical(; G, R, S, insertstep, transitions, rtarget, rinit, nsamples, onstates, totaltime, ntrials, fittedparam, propcv, cv, interval, noisepriors, hierarchical, method, maxtime, nchains)
```

階層モデルを使用してシミュレーションされたトレースデータセットをフィットし、ターゲットと比較します。

# 引数

  * `G`, `R`, `S`, `insertstep`, `transitions`: モデル構造。
  * `rtarget`, `rinit`: レートパラメータ。
  * `nsamples`, `onstates`, `totaltime`, `ntrials`: データおよびシミュレーションオプション。
  * `fittedparam`, `propcv`, `cv`, `interval`, `noisepriors`, `hierarchical`, `method`, `maxtime`, `nchains`: フィッティングオプション。

# 戻り値

  * (中央値フィットパラメータ, ターゲットパラメータ) のタプル。
