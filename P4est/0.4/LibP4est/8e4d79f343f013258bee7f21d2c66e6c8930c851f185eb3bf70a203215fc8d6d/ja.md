```
sc_array_copy(dest, src)
```

1つの配列の内容を別の配列にコピーします。両方の配列は同じ要素サイズでなければなりません。ソース配列はビューである可能性があります。memcpy (3) を使用します: 2つの配列が重なる場合、結果は未定義です。

### パラメータ

  * `dest`:[in] 配列（ビューではない）がサイズ変更され、新しいデータを取得します。
  * `src`:[in] 新しいデータのソースとして使用される配列で、変更されません。

### プロトタイプ

```c
void sc_array_copy (sc_array_t * dest, sc_array_t * src);
```
