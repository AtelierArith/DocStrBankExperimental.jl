```
solve(prob::SciMLBase.AbstractSteadyStateProblem,
      alg::CTKAlg;
      nrm=norm,
      τstop=1e12*365*24*60*60,
      preprint="",
      maxItNewton=50)
```

`prob`をC.T.Kelleyのシャマンスキー法アルゴリズムのAIBECSカスタマイズ版を使用して解決します。
