```
getindex_ref(collection, offset, stride, T, ref_type, idx)
```

`collection`（`Sections`、`DynamicLinks`など）を指定し、与えられた`offset`、`stride`、および`T`パラメータを使用して、インデックス`idx`に位置する`ref_type`オブジェクトを読み取り、構築します。例の呼び出し：

```
getindex_ref(
    sections,
    section_header_offset(oh),
    section_header_size(oh),
    section_header_type(oh),
    SectionRef,
    idx
)
```
