```
sc_array_new_view(array, offset, length)
```

既存の [`sc_array_t`](@ref) の新しいビューを作成します。

### パラメータ

  * `array`:[in] ビューが生存している間、配列はサイズ変更されてはいけません。
  * `offset`:[in] ビューされたセクションのオフセット（要素単位）。このオフセットは、ビューがリセットされるまで変更できません。
  * `length`:[in] ビューされたセクションの長さ（要素単位）。ビューはこの長さを超えてサイズ変更できません。

### プロトタイプ

```c
sc_array_t *sc_array_new_view (sc_array_t * array, size_t offset, size_t length);
```
