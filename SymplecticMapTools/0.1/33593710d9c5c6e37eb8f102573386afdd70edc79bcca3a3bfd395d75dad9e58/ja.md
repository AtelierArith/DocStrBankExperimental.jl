```
ConnectingOrbit(Na::Integer, p::Integer)
```

`p` セグメント cⱼ : [0,1] -> R² からなる接続軌道を初期化します。端点 cⱼ(0) と cⱼ(1) はどちらも双曲線周期軌道です。接続軌道はこれらを接続し、島の外境界として機能します。接続軌道は次数 `Na` のチェビシェフ多項式によってパラメータ化されます。

接続軌道を初期化し計算するための関数については `linear_initial_connecting_orbit` と `gn_connecting!` を参照してください。
