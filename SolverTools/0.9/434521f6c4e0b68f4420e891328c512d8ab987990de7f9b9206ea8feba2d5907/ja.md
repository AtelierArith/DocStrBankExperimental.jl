```
ared, pred = aredpred(tr, nlp, f, f_trial, Δm, x_trial, step, slope)
ared, pred = aredpred(tr, nls, Fx, f, f_trial, Δm, x_trial, step, slope)
```

実際の削減 `∆f` と予測された削減 `Δm` を計算します。ここで `ared = Δf = f_trial - f` は目的関数/メリット関数/ペナルティ関数の実際の削減であり、`pred = Δm = m_trial - m` はモデル `m` によって予測された削減です。`m` が最小化されていると仮定し、したがって `Δm < 0` であるとします。

`tr.good_grad` が `true` の場合、`x_trial` における `nlp` の勾配は `tr.gt` に保存されます。`AbstractNLSModel` の場合、引数 `Fx` は勾配が更新された場合の残差を保存します。
