```
エイリアス
```

GraphQLフィールドまたはクエリのエイリアスを含みます。`Alias`は、`output_fields`キーワード引数で使用できるほか、クエリ、ミューテーション、サブスクリプション名の代わりに直接使用することもできます。

# 例

クエリ名の代わりに`Alias`を使用する：

```jldoctest alias_label; setup=:(using GraphQLClient)
julia> client = Client("https://countries.trevorblades.com");

julia> alias = Alias("country_alias", "country");

julia> query(client, alias, query_args=Dict("code"=>"BR"), output_fields=["name"]).data
Dict{String, Any} with 1 entry:
  "country_alias" => Dict{String, Any}("name"=>"Brazil")

```

`output_fields`で`Alias`を使用する：

```jldoctest alias_label; setup=:(using GraphQLClient)
julia> field_alias = Alias("country_name_alias", "name");

julia> query(client, "country", query_args=Dict("code"=>"BR"), output_fields=[field_alias]).data
Dict{String, Any} with 1 entry:
  "country" => Dict{String, Any}("country_name_alias"=>"Brazil")
```
