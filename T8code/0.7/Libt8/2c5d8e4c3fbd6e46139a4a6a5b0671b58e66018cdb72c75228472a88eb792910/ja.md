```
t8_element_array_init_data(view, base, scheme, elem_count)
```

与えられたプレーンCデータ（[`t8_element_t`](@ref)の配列）から、すでに割り当てられた（または静的な）ビューを初期化します。返される配列ビューは[`t8_element_array_reset`](@ref)を必要としません（ただし、呼び出しても問題ありません）。

# 引数

  * `view`:[in,out] 初期化される配列構造。
  * `base`:[in] ビューが生存している間、データは移動されてはいけません。*scheme*に対応する[`t8_element_t`](@ref)の配列でなければなりません。
  * `scheme`:[in] *base*に格納されている要素のeclassスキーム。
  * `elem_count`:[in] 要素単位でのビューの長さ。この長さを超えるようにビューをサイズ変更することはできません。後で[`t8_element_array_reset`](@ref)を呼び出す必要はありません。

### プロトタイプ

```c
void t8_element_array_init_data (t8_element_array_t *view, t8_element_t *base, t8_eclass_scheme_c *scheme, size_t elem_count);
```
