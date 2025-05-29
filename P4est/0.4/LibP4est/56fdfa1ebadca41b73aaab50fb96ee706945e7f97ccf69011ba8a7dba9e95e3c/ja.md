```
sc_array_init_view(view, array, offset, length)
```

既に割り当てられた（または静的な）ビューを既存の [`sc_array_t`](@ref) から初期化します。返される配列ビューは [`sc_array_reset`](@ref) を必要としません（ただし、呼び出しても問題ありません）。

### パラメータ

  * `view`:[in,out] 初期化される配列構造体。
  * `array`:[in] ビューが生存している間、配列はサイズ変更されてはいけません。
  * `offset`:[in] 要素単位でのビューされたセクションのオフセット。このオフセットは、ビューがリセットされるまで変更できません。
  * `length`:[in] 要素単位でのビューの長さ。この長さを超えるようにビューをサイズ変更することはできません。後で [`sc_array_reset`](@ref) を呼び出す必要はありません。

### プロトタイプ

```c
void sc_array_init_view (sc_array_t * view, sc_array_t * array, size_t offset, size_t length);
```
