```
sc_array_init_data(view, base, elem_size, elem_count)
```

与えられたプレーンCデータから、すでに割り当てられた（または静的な）ビューを初期化します。返される配列ビューは[`sc_array_reset`](@ref)を必要としません（ただし、呼び出しても問題ありません）。

### パラメータ

  * `view`:[in,out] 初期化される配列構造。
  * `base`:[in] ビューが生存している間、データは移動されてはいけません。
  * `elem_size`:[in] 配列要素1つのサイズ（バイト単位）。
  * `elem_count`:[in] 要素単位でのビューの長さ。この長さを超えるようにビューをサイズ変更することはできません。後で[`sc_array_reset`](@ref)を呼び出す必要はありません。

### プロトタイプ

```c
void sc_array_init_data (sc_array_t * view, void *base, size_t elem_size, size_t elem_count);
```
