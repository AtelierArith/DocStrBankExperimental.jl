```
sc_array_copy_into(dest, dest_offset, src)
```

別の配列の一部に1つの配列の内容をコピーします。両方の配列は同じ要素サイズでなければなりません。どちらの配列もビューである可能性があります。宛先配列は十分な大きさでなければなりません。memcpy (3) を使用します: 2つの配列が重なる場合、結果は未定義です。

### パラメータ

  * `dest`:[in] 書き込まれる配列。要素数は少なくとも **dest_offset** + **src**->elem_count でなければなりません。
  * `dest_offset`:[in] **dest** 配列で上書きされる最初のインデックス。すべてのインデックスと同様に、要素を指し、バイトではありません。
  * `src`:[in] 新しいデータのソースとして使用される配列、変更されません。

### プロトタイプ

```c
void sc_array_copy_into (sc_array_t * dest, size_t dest_offset, sc_array_t * src);
```
