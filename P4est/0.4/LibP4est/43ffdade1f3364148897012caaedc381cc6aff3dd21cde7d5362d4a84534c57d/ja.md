```
sc_array_move_part(dest, dest_offset, src, src_offset, count)
```

メモリ移動 (3) を使用して、1 つの配列の一部を別の配列にコピーします。両方の配列は同じ要素サイズでなければなりません。どちらの配列もビューである可能性があります。宛先配列は十分な大きさでなければなりません。メモリ移動 (3) を使用します：2 つの配列は重なっている可能性があります。

### パラメータ

  * `dest`:[in] 書き込まれる配列。要素数は少なくとも **dest_offset** + **count** でなければなりません。
  * `dest_offset`:[in] **dest** 配列で上書きされる最初のインデックス。すべてのインデックスと同様に、バイトではなく要素を指します。
  * `src`:[in] 読み取られる配列。要素数は少なくとも **src_offset** + **count** でなければなりません。
  * `src_offset`:[in] **src** 配列で使用される最初のインデックス。すべてのインデックスと同様に、バイトではなく要素を指します。
  * `count`:[in] コピーされるエントリの数。

### プロトタイプ

```c
void sc_array_move_part (sc_array_t * dest, size_t dest_offset, sc_array_t * src, size_t src_offset, size_t count);
```
