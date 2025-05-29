```
RiskEvent(Prob, Distribution, Trials; seed=0)
```

リスクイベントは、0を膨張させる条件付き分布として定義されます。

RiskEvent()は、定義された試行回数だけ任意の分布を条件付きでサンプリングすることを可能にします。 *Prob*は、影響分布をサンプリングする条件付き確率です。 *Distribution*は、Distributions.jlからの任意の単変量分布です。 *Trials*は、総反復回数です。 *seed*は、RiskEventのためのシードを設定することを可能にします。 空白のままか0に設定すると、シードはランダムに設定されます。
