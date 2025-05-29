```
p8est_ghost_t
```

ローカルドメインに隣接する四分木

| フィールド                     | 注釈                                                                                              |
|:------------------------- |:----------------------------------------------------------------------------------------------- |
| btype                     | どの隣接がゴーストレイヤーにあるか                                                                               |
| ghosts                    | [`p8est_quadrant_t`](@ref) 型の配列                                                                 |
| tree_offsets              | num_trees + 1 ゴーストインデックス                                                                        |
| proc_offsets              | mpisize + 1 ゴーストインデックス                                                                          |
| mirrors                   | [`p8est_quadrant_t`](@ref) 型の配列                                                                 |
| mirror*tree*offsets       | num_trees + 1 ミラーインデックス                                                                         |
| mirror*proc*mirrors       | 外部プロセッサランクによってグループ化されたミラーのインデックス、各ランク内で昇順                                                       |
| mirror*proc*offsets       | mpisize + 1 mirror*proc*mirrors へのインデックス                                                        |
| mirror*proc*fronts        | mirror*proc*mirrors のようなものですが、最外層の八分木に制限されています。これは [`p8est_ghost_expand`](@ref) が呼ばれるまで NULL です |
| mirror*proc*front_offsets | [`p8est_ghost_expand`](@ref) が呼ばれるまで NULL                                                       |
