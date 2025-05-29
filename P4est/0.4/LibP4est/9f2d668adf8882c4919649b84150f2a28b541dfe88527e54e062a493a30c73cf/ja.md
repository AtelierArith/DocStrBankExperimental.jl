```
p4est_iter_corner_info
```

ユーザー定義の [`p4est_iter_corner_t`](@ref) コールバックに利用可能な情報。

tree*boundary が false の場合、コーナーはツリーの内部にあります。tree*boundary が false の場合、sides[0] にはコーナーに接触する最も低い z-order の象限が含まれます。tree*boundary が true の場合、その値はコーナーのツリーに対する位置に応じて P4EST*CONNECT_FACE/CORNER になります。

| フィールド         | 注釈                                      |
|:------------- |:--------------------------------------- |
| tree_boundary | boolean: 内部面 (0)、ツリー境界面 (true)          |
| sides         | [`p4est_iter_corner_side_t`](@ref) 型の配列 |
