```
creepcomp(m[, t, params])
```

与えられたモデル m のクリープコンプライアンス (J) へのアクセスを提供します。幅広い入力と共に使用できます。

時間値が提供されると（または時間値の配列が提供されると）、関数は対応するクリープコンプライアンスの値を返します。

```
creepcomp(m::RheoModel, time (単一値または配列))

creepcomp(m::RheoModelClass, time (単一値または配列), parameters (配列、名前付きタプルまたはキーワードパラメータ))
```

例:

```
creepcomp(Maxwell, 1, k=1., η=1)

creepcomp(Maxwell, [1,2,3], [1,1])
```

時間値が提供されない場合、creepcomp はクリープコンプライアンス関数自体を返します。

```
creepcomp(m::RheoModel)

creepcomp(m::RheoModelClass, parameters (配列、名前付きタプルまたはキーワードパラメータ))
```

例:

```
m = RheoModel(Maxwell, k=1., η=1)
J = creepcomp(m)
J([0,1,2])
```
