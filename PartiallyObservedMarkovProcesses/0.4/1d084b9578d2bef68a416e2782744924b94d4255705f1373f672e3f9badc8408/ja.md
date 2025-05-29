```
rinit(object; t0=timezero(object), params=coef(object), nsim=1)
```

`rinit`は初期状態分布のシミュレーターの作業馬です。

## 引数

  * `object`: PompObject
  * `params`: パラメータのNamedTupleまたはNamedTuplesのベクトル
  * `t0`: `rinit`がシミュレートされる時間。この値は単一のスカラーである必要があります。
  * `nsim`: 希望するシミュレーションの数。
