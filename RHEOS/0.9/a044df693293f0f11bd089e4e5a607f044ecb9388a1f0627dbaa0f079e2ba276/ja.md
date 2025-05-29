```
relaxmod(m[, t, params])
```

指定されたモデル m の緩和モジュラス (G) へのアクセスを提供します。幅広い入力と共に使用できます。

時間値が提供されると（または時間値の配列が提供されると）、関数は対応する緩和モジュラスの値を返します。

```
relaxmod(m::RheoModel, time (single value or array))

relaxmod(m::RheoModelClass, time (single value or array), parameters (array, named tupple or keyword parameters))
```

例:

```
relaxmod(Maxwell, 1, k=1., η=1)

relaxmod(Maxwell, [1,2,3], [1,1])
```

時間値が提供されない場合、relaxmod は緩和関数自体を返します。

```
relaxmod(m::RheoModel)

relaxmod(m::RheoModelClass, parameters (array, named tupple or keyword parameters))
```

例:

```
m = RheoModel(Maxwell, k=1., η=1)
G = relaxmod(m)
G([0,1,2])
```
