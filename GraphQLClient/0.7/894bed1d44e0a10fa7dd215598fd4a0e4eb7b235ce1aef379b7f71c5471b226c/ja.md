```
@gql_str(document, throw_on_error=true)
```

GraphQLクエリ文字列を作成し、オプションで検証します。

文字列はGraphQLParser.jlによって解析され、半分検証されます。サーバーからのスキーマを必要としない検証が行われます。詳細についてはGraphQLParserのドキュメントを参照してください。

解析エラーは常にスローされますが、他の検証エラーは2番目の引数を使用してオフにすることができます。

このマクロを使用する追加の利点は、ドル記号をエスケープする必要がないことです（以下の例を参照）。

# 例

一般的な使用法

```julia-repl
julia> client = Client("https://countries.trevorblades.com");

julia> str = gql"""
query($code: ID!){
    country(
        code:$code
    ){
        name
    }
}
""";

julia> variables = Dict("code" => "BR");

julia> GraphQLClient.execute(client, str; variables=variables)
GraphQLClient.GQLResponse{Any}
  data: Dict{String, Any}
          country: Dict{String, Any}
```

解析エラー

```julia-repl
julia> str = gql"""
query(code: ID!){  # 変数名の前に$がない
    country(
        code:$code
    ){
        name
    }
}
""";

# ERROR: LoadError: ArgumentError: invalid GraphQL string at byte position 7 while parsing
#     Variable name must start with '$'
#     query(code: ID!){  # 変数名の前に 
#           ^
```

検証エラー

```julia-repl
julia> str = gql"""
{
    countries{
        name
    }
}

query{  # 匿名操作があるときに別の操作を持つことはできません
    countries{
        name
    }
}
""";
# ERROR: LoadError: Validation Failed

# GraphQLParser.AnonymousOperationNotAlone
#       message: This anonymous operation must be the only defined operation.
#      location: Line 1 Column 1
```

検証をオフにする

```julia-repl
julia> str = @gql_str """
{
    countries{
        name
    }
}

query{  # 匿名操作があるときに別の操作を持つことはできません
    countries{
        name
    }
}
""" false
# エラーなし
```
