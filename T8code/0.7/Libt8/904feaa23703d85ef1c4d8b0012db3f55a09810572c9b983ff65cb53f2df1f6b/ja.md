```
t8_forest_ghost_exchange_data(forest, element_data)
```

ユーザー定義の要素データのゴースト情報を交換します。

!!! note
    この関数は集団的であり、したがってフォレストのMPIコミュニケーター内のすべてのプロセスによって呼び出される必要があります。


# 引数

  * `forest`:[in] フォレスト。コミットされている必要があります。
  * `element_data`:[in] *forest*内の各ローカル要素とゴーストのために1つの値を格納する長さnum*local*elements + num*ghostsの配列。この関数を呼び出した後、ゴースト要素のエントリは対応する所有プロセスの*element*data*配列のエントリで更新されます。

### プロトタイプ

```c
void t8_forest_ghost_exchange_data (t8_forest_t forest, sc_array_t *element_data);
```
