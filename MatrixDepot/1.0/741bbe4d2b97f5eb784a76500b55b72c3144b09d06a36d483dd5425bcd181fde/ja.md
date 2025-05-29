```
keyword(word::Union{AbstractString,Tuple,Vector})
```

述語関数は、`word`がテキストメタデータフィールド `[:notes, :title, :kind, :author]` のいずれかに含まれているかどうかをチェックします。タプルとベクターはそれぞれ `AND` および `OR` として解釈されます。
