```
Dict(rec::Record)
```

`Record`とそのプロパティを`Dict`に抽出します。

!!! warn
    `AttributeRecord`に対しては、これは高コストな操作になる可能性があるため、すべてのログレコードに対してこれを行うことはお勧めしません。すべての`Attribute`を使用する予定がない限り。

