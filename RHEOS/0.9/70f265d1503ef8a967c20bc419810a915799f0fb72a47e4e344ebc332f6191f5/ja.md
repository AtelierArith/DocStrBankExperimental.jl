```
lossmod(m[, ω, params])
```

与えられたモデル m の損失弾性率 (G'') へのアクセスを提供します。

周波数値が提供されると（または周波数値の配列）、関数は損失弾性率の対応する値を返します。

```
lossmod(m::RheoModel, frequency (single value or array))

lossmod(m::RheoModelClass, frequency (single value or array), parameters (array, named tupple or keyword parameters))
```

例:

```
lossmod(Maxwell, 1, k=1., η=1)

lossmod(Maxwell, [1,2,3], [1,1])
```

時間値が提供されない場合、lossmod は損失弾性率関数自体を返します。

```
lossmod(m::RheoModel)

lossmod(m::RheoModelClass, parameters (array, named tupple or keyword parameters))
```

例:

```
m = RheoModel(Maxwell, k=1., η=1)
Gpp = lossmod(m)
Gpp([0,1,2])
```
