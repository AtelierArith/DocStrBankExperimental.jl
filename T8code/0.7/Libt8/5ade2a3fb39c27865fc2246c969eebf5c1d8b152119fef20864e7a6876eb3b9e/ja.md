```
t8_forest_get_first_local_element_id(forest)
```

フォレストの最初のローカル要素のグローバルインデックスを計算します。この関数はコレクティブです。

# 引数

  * `forest`:[in] 最初の要素のインデックスが計算されるコミットされたフォレスト。

# 戻り値

*forest* の最初のローカル要素のグローバルインデックス。 この関数を呼び出すとき、フォレストはコミットされている必要があります。この関数はコレクティブであり、各プロセスで呼び出す必要があります。

### プロトタイプ

```c
t8_gloidx_t t8_forest_get_first_local_element_id (t8_forest_t forest);
```
