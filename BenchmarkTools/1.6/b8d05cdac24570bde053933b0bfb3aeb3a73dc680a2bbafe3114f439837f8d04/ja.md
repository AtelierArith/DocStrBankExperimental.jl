```
judge(target::TrialEstimate, baseline::TrialEstimate; [time_tolerance::Float64=0.05])
```

最初の推定値 `target` が、2番目の推定値 `baseline` に対して回帰を示すのか、改善を示すのかを報告します。
