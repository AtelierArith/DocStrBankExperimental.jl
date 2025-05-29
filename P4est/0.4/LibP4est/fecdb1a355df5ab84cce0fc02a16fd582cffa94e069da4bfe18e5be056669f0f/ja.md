```
p4est_iter_face_info
```

ユーザー定義の [`p4est_iter_face_t`](@ref) コールバックに利用可能な情報。

オリエンテーションは、顔が1つの木の中にある場合は0です。それ以外の場合は、接続性で与えられた2つの木の間のオリエンテーション値と同じです。顔が森の外部境界にある場合、側面は1つだけです。tree*boundary が false の場合、顔は木の内部にあります。tree*boundary が false の場合、sides[0] には顔に接触する最も低い z-順序の象限が含まれます。tree*boundary が true の場合、その値は P4EST*CONNECT_FACE です。

| フィールド         | 注釈                                                   |
|:------------- |:---------------------------------------------------- |
| orientation   | [`p4est_connectivity_t`](@ref) の定義における側面同士のオリエンテーション |
| tree_boundary | ブール値: 内部の顔 (0)、木の境界の顔 (true)                         |
