```
aws_http_headers_get_index(headers, index, out_header)
```

指定されたインデックスのヘッダーを取得します。特定のヘッダーのインデックスは、ヘッダーが変更されるたびに変わる可能性があります。ヘッダーを反復処理する際には、以下の順序規則が適用されます：

  * 同じ名前のヘッダーは、常に互いに対して同じ順序になります。「A: one」が「A: two」の前に追加されると、「A: one」は常に「A: two」の前に来ます。
  * 異なる名前のヘッダーは、互いに対して任意の順序になる可能性があります。「A: one」が1回目の反復で「B: bee」の前に見られた場合、次の反復では「B: bee」が「A: one」の前に見られることがあります。

インデックスが無効な場合、AWS*ERROR*INVALID_INDEXが発生します。

### プロトタイプ

```c
int aws_http_headers_get_index( const struct aws_http_headers *headers, size_t index, struct aws_http_header *out_header);
```
