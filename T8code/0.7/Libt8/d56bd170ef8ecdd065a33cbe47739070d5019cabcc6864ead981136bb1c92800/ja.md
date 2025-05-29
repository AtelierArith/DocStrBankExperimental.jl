```
t8_element_array_init_view(view, array, offset, length)
```

既に割り当てられた（または静的な）t8*element*arrayから既存のビューを初期化します。返される配列ビューは[`t8_element_array_reset`](@ref)を必要としません（ただし、呼び出しても問題ありません）。

# 引数

  * `view`:[in,out] 初期化される配列構造。
  * `array`:[in] ビューが生存している間、配列はサイズ変更されてはいけません。
  * `offset`:[in] 要素単位でのビューされたセクションのオフセット。このオフセットは、ビューがリセットされるまで変更できません。
  * `length`:[in] 要素単位でのビューの長さ。この長さを超えるようにビューをサイズ変更することはできません。後で[`sc_array_reset`](@ref)を呼び出す必要はありません。

### プロトタイプ

```c
void t8_element_array_init_view (t8_element_array_t *view, t8_element_array_t *array, size_t offset, size_t length);
```
