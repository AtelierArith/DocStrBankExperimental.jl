```
sc_array_split(array, offsets, num_types, type_fn, data)
```

配列内の列挙可能な型のグループのオフセットを計算します。

### パラメータ

  * `array`:[in] 型によって昇順にソートされた配列。k が *array* のインデックスである場合、0 <= *type_fn* (*array*, k, *data*) < *num_types* です。
  * `offsets`:[in,out] *num_types* + 1 エントリにリサイズされる初期化された size_t 型の配列。型 k のオブジェクトを含む *array* のインデックス j は *offsets*[k] <= j < *offsets*[k + 1] です。型 k のオブジェクトが存在しない場合、*offsets*[k] = *offset*[k + 1] です。
  * `num_types`:[in] *array* 内のオブジェクトの可能な型の数。
  * `type_fn`:[in] 配列内のオブジェクトの型を返します。
  * `data`:[in] *type_fn* に渡される任意のユーザーデータ。

### プロトタイプ

```c
void sc_array_split (sc_array_t * array, sc_array_t * offsets, size_t num_types, sc_array_type_t type_fn, void *data);
```
