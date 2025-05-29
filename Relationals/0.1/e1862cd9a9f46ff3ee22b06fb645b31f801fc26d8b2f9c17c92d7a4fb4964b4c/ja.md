```
@belongs_to(model_type::QuoteNode, attr_name::Expr)
```

モデルオブジェクトにマッピングされた単一のオブジェクトを取得するための「get{attr_name}」という名前の関数を生成します。

## 例

```julia
# Userオブジェクトのために「getaddress」関数を設定します。
@belongs_to User :address

# Manufacturerオブジェクトのために「getadmin」関数を設定します。
@belongs_to Manufacturer :admin=>User
```

```julia
# ユーザーの住所を取得します。
julia> getaddress(first(User))
Address(1, "1 Bagshot Row", "Shire", "Middle Earth", "37012")

# 製造業者の所在地を取得します。
julia> getadmin(first(Manufacturer, 1))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")
```
