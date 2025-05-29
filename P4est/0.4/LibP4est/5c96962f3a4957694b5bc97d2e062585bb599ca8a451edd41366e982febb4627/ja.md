```
p8est_iter_volume_info
```

ユーザー定義の [`p8est_iter_volume_t`](@ref) コールバック関数で利用可能な情報。

*treeid* は、*quad* が属する木の `p4est`->trees 内のインデックスを示します。*quadid* は、*tree* の四分木配列内の *quad* のインデックスを示します。

| フィールド  | 注記                                            |
|:------ |:--------------------------------------------- |
| quad   | コールバックの四分木                                    |
| quadid | *quad* の木配列内の ID (参照: [`p8est_tree_t`](@ref)) |
| treeid | *quad* を含む木                                   |
