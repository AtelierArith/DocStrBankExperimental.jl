```
t8_forest_ghost_create_balanced_only(forest)
```

森林のためのゴースト要素の1層を作成します。このバージョンはバランスの取れた森林でのみ機能し、p4estからの元のアルゴリズムです：スケーラブルなアルゴリズムは、オクトリーの森林上での並列適応メッシュリファインメントのためのものです。

!!! note
    ユーザーはバランスの取れた森林に対しても t8*forest*ghost_create を優先すべきです。


# 引数

  * `forest`:[in,out] バランスの取れた森林/*forest*は、この関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
void t8_forest_ghost_create_balanced_only (t8_forest_t forest);
```
