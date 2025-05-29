```
@has_many(model_type::QuoteNode, attr_name::Expr)
```

モデルオブジェクトにマッピングされたオブジェクトのコレクションを取得するために「get{attr_name}」という名前の関数を生成します。

## 例

```julia
# 製造業者オブジェクトのために「getproducts」関数を設定します。
@has_many Manufacturer :products

# 製造業者オブジェクトのために「getadmins」関数を設定します。
@has_many Manufacturer :admins=>User
```

```julia
# 製造業者のすべての製品を取得します。
julia> getproducts(first(Manufacturer))
2-element Vector{Product}:
  Product(1, "フライパン")
  Product(2, "パイプウィード")

# 製造業者のすべての管理者を取得します。
julia> getadmins(first(Manufacturer))
2-element Vector{User}:
  User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "ビルボ", "バギンズ")
  User(2, UUID("0bb0cdc4-b1d3-43ac-93ad-693a94fc9ceb"), "フロド", "バギンズ")
```
