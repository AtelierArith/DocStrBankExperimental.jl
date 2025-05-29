```
Options(object;
    filename::Union{AbstractString,Nothing,Missing}=missing,
    caption::Union{AbstractString,Nothing,Missing}=missing,
    label::Union{AbstractString,Nothing,Missing}=missing)
```

`object`と結果のドキュメントに渡されるいくつかのメタ情報を含む構造体です。`caption`と`label`オプションは`pandoc-crossref`によって使用されます。
