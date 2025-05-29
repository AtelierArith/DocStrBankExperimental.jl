```
t8_forest_partition_test_boundary_element(forest)
```

現在のランクの最後の要素の最後の子孫が、ランク+1の保存された最初の子孫よりも小さい線形IDを持っているかどうかをテストします。これが成り立たない場合、要素が重なっています。

!!! note
    *forest* はこの関数を呼び出す前にコミットされている必要があります。


# 引数

  * `forest`:[in] 森。

### プロトタイプ

```c
void t8_forest_partition_test_boundary_element (const t8_forest_t forest);
```
