```
q_opt(anp::AbstractNewsvendorProblem; rounded = true)
```

ニュースベンダー問題の期待利益を最大化する数量を計算します（すなわち、クリティカルフラクタイルが在庫確率に等しい場合）。解決を試みます 

$$
F(q_{opt}) = \textrm{critical fractile} 
$$

ここで、Fは需要分布の累積分布関数（c.d.f.）です。`rounded=false`でない限り、最も近い次の整数を返します。そうでない場合は、正確な実数を返します。q*minおよびq*maxで制限されます。
