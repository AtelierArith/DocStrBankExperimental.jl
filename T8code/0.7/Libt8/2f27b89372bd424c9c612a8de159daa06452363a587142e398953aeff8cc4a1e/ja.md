```
t8_forest_partition_data(forest_from, forest_to, data_in, data_out)
```

配分されたフォレストに従って配列を再配分します。

!!! note
    *data_in* は *forest_from* のローカル要素の数と同じサイズでなければなりません。 *data_out* はすでに割り当てられており、*forest_to* のローカル要素の数と同じサイズでなければなりません。


# 引数

  * `forest_form`:[in] 配分ステップの前のフォレスト。
  * `forest_to`:[in] *forest_from* の配分されたフォレスト。
  * `data_in`:[in] *forest_from* に従ってデータを保持する [`sc_array_t`](@ref) へのポインタ（要素ごとに1つの値）。
  * `data_out`:[in,out] *forest_to* に従ってデータを保持できるようにすでに割り当てられた [`sc_array_t`](@ref) へのポインタ。

### プロトタイプ

```c
void t8_forest_partition_data (t8_forest_t forest_from, t8_forest_t forest_to, const sc_array_t *data_in, sc_array_t *data_out);
```
