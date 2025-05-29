```
sat_prob(root::LogicCircuit; varprob::Function)::Rational{BigInt}
```

回路を満たすランダムな世界の確率を取得します。各変数の確率は、デフォルトで1/2の`varprob`関数によって与えられます。
