```
is_mutation_free_argtype(argtype) -> Bool
```

`argtype` オブジェクトがミューテーションフリーである場合は `true` を返します。これは、この型自体または任意のフィールドを通じてミュータブルなメモリにアクセスできないことを意味します（`Base.ismutationfree` を参照）。このクエリは特に `:inaccessiblememonly` 効果プロパティを分析するために書かれており、ミューテーションフリーのグローバルオブジェクトへのアクセスがある場合に `:inaccessiblememonly` プロパティを汚染しないことで分析の精度を向上させることを目的としています。
