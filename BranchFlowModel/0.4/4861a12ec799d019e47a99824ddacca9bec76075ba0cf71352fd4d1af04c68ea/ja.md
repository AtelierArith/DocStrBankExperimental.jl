```
add_linear_variables(m, net::Network{MultiPhase})
```

次のための実数位相ベクトル変数を定義します：

  * `:vsqrd` バス電圧の大きさの二乗
  * `:pij`, `:qij` ブランチの電力フロー
  * `:p`, `:q` スラックバスのネット電力注入
