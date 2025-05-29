```
 ClimaLand.make_compute_exp_tendency(component::AbstractCanopyComponent, canopy)
```

キャノピー `component` のために compute*exp*tendency!(dY,Y,p,t) 関数を作成します。

コンポーネントモデルは独立したモデルではないため、他の情報が必要であり、（`canopy` モデル自体を介して）渡される場合があります。全体のキャノピーモデルの右辺は、個々のコンポーネントのためにこれらの関数を利用することができます。
