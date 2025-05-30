```
fetch(api::API, kwargs...)
```

JQuants APIからデータを取得します。

# 引数

  * `api::API`: データを取得するためのAPI構造体
  * `json::Bool`: trueの場合、未加工のJSON文字列のベクターを返します。ベクターの要素数はAPIレスポンスのページ数に等しいです。falseの場合、DataFrameを返します。デフォルトはfalseです。

# 例

```julia
julia> fetch(ListedInfo(code="72030"));

julia> fetch(ListedInfo(code="72030"), json=true);
```
