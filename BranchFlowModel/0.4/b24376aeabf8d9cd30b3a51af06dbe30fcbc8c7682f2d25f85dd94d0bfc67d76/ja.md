```
add_linear_variables(m, net::Network{SinglePhase})
```

単相線形モデルのための変数を追加します：

  * `Pij` と `Qij` はすべての `edges(net)`
  * `p0` と `q0` スラックバスの電力
