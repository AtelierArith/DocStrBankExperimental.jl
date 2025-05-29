```
dynamicmod(m[, ω, params])
```

与えられたモデル m の複素動的弾性率 (G' + i G'') へのアクセスを提供します。

  * 周波数値 (または周波数値の配列) が提供されると、関数は複素動的弾性率の対応する値を返します。

    dynamicmod(m::RheoModel, frequency (単一値または配列))

    dynamicmod(m::RheoModelClass, frequency (単一値または配列), parameters (配列、名前付きタプルまたはキーワードパラメータ))

例:

```
dynamicmod(Maxwell, 1, k=1., η=1)

dynamicmod(Maxwell, [1,2,3], [1,1])
```

  * 時間値が提供されない場合、lossmod は複素動的弾性率関数自体を返します。

    dynamicmod(m::RheoModel)

    dynamicmod(m::RheoModelClass, parameters (配列、名前付きタプルまたはキーワードパラメータ))

例:

```
m = RheoModel(Maxwell, k=1., η=1)
Gd = dynamicmod(m)
Gd([0,1,2])
```

注意: abs() と angle() を使用して、複素弾性率の大きさと位相を取得します。
