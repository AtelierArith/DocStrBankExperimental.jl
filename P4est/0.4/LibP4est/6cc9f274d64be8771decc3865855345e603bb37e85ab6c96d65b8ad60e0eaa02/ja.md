```
p8est_iter_face_info
```

ユーザー定義の [`p8est_iter_face_t`](@ref) コールバックに利用可能な情報。

面が1つの木の内部にある場合、向きは0です。それ以外の場合、接続性で与えられた2つの木の間の向きの値と同じです。面が森の外側にある場合、側面は1つだけです。tree*boundary が false の場合、面は木の内部にあります。tree*boundary が false の場合、sides[0] には面に接触する最も低い z-order の象限が含まれます。tree*boundary が true の場合、その値は P8EST*CONNECT_FACE です。

| フィールド         | 注釈                                            |
|:------------- |:--------------------------------------------- |
| orientation   | [`p8est_connectivity_t`](@ref) の定義における側面同士の向き |
| tree_boundary | ブール値: 内部面 (0)、木の境界面 (true)                    |
