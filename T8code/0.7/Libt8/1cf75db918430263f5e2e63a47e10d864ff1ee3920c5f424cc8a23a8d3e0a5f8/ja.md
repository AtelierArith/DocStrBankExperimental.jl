```
t8_forest_ghost_create_balanced_only(forest)
```

森林のためのゴースト要素の1層を作成します。このバージョンはバランスの取れた森林でのみ機能し、p4estからの元のアルゴリズムです：スケーラブルなアルゴリズムによる並列適応メッシュリファインメントのためのオクトリーの森林上

!!! note
    ユーザーはバランスの取れた森林に対しても t8*forest*ghost_create を優先すべきです。


# 引数

  * `forest`:[in,out] バランスの取れた森林/*forest*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
void t8_forest_ghost_create_balanced_only (t8_forest_t forest);
```
