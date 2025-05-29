```
simulate_array(object; nsim = 1, params, rinit, rprocess, rmeasure, args...)
```

POMPをシミュレートします。少なくとも`rinit`、`rprocess`、および`rmeasure`の基本コンポーネントが必要です。シミュレートされたサンプルパスを含む配列を返します。
