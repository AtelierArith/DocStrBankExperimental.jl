```
occurrence_count(species::Species; kw...)
occurrence_count(; kw...)
```

分類群の出現回数をカウントします。

# 例

```
juila> sp = species_match("Pteropus niger");

juila> occurrence_count(sp)
559
```

# キーワード

  * `taxonKey`: `Species`が渡されない場合に最も便利なキーです。

出現回数には許可されるキーワードの組み合わせの複雑なスキーマがあります。これらは`GBIF2.occurrence_count_schema()`を使用してGBIF APIからアクセスできます。
