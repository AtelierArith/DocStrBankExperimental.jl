```
t8_forest_set_ghost_ext(forest, do_ghost, ghost_type, ghost_version)
```

t8*forest*set*ghostと同様ですが、ゴーストアルゴリズムを変更するための追加オプションがあります。これはアルゴリズムのデバッグとタイミングに使用されます。アプリケーションはほとんど常にt8*forest*set*ghostを使用するべきです。

# 引数

  * `ghost_version`:[in] 1の場合、バランスの取れた森林のための反復ゴーストアルゴリズムが使用されます。2の場合、バランスの取れていない森林のための反復アルゴリズム。3の場合、バランスの取れていない森林のためのトップダウン探索アルゴリズム。

# 参照

[`t8_forest_set_ghost`](@ref)

### プロトタイプ

```c
void t8_forest_set_ghost_ext (t8_forest_t forest, int do_ghost, t8_ghost_type_t ghost_type, int ghost_version);
```
