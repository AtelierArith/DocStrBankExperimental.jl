```
(headers, queries, basicauth)
```

提供:

  * `headers::NamedTuple` すべてのリクエストヘッダー
  * `queries::NamedTuple` すべてのリクエストクエリパラメータ
  * `basicauth::Function` 見つかった場合は NamedTuple(username, password) を返し、見つからない場合は `nothing` を返す

`basicauth` は最初にヘッダー内の basicauth 詳細を探し、次にパラメータを探し、最初に見つかったものを返すか `nothing` を返します。

オプションで、`basicauth` に2つのパラメータを渡すことができます:

`basicauth([usernamekey::String, passwordkey::String])`

これは、どのクエリパラメータを探すかを定義します。デフォルトは `("username","password")` です。

# 例:

```julia
function authfunction(details::RequestDetails)
    headers = details.headers
    queries = details.queries
    auth = details.basicauth()

    auth !== nothing && return auth.username === username && auth.password === password
    return false 
end
```
