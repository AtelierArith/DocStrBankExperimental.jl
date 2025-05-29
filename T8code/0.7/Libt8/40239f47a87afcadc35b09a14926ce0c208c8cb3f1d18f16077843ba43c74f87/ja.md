```
t8_element_array_copy(dest, src)
```

配列の内容を別の配列にコピーします。両方の配列は同じ eclass_scheme を持っている必要があります。

# 引数

  * `dest`:[in] 配列はサイズ変更され、新しいデータを取得します。
  * `src`:[in] 新しいデータのソースとして使用される配列で、変更されません。

### プロトタイプ

```c
void t8_element_array_copy (t8_element_array_t *dest, const t8_element_array_t *src);
```
