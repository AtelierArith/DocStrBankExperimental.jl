```
t8_forest_no_overlap(forest)
```

フォレストにローカルな重複要素があるかどうかを確認します。

!!! note
    この関数は集団的ですが、各プロセスでのローカルな重複のみをチェックします。


# 引数

  * `forest`:[in] 考慮すべきフォレスト。

# 戻り値

*forest* が互いに重なり合う要素を持たない場合は真を返します。

# 参照

[`t8_forest_partition_test_boundary_element`](@ref) は、プロセス境界を越えたグローバルな重複をテストしたい場合に使用してください。

### プロトタイプ

```c
int t8_forest_no_overlap (t8_forest_t forest);
```
