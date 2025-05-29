```
GQLEnum
```

`direct_write=true`をクエリやミューテーションで使用する場合、ENUMはこのタイプでラップする必要があります。そうしないと、クエリ文字列内で引用符でラップされてしまいます。

詳細や例については、[`directly_write_query_args`](@ref)を参照してください。
