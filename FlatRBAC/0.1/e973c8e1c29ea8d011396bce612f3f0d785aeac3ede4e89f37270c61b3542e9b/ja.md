```
Permission(str::String, description::String="")
```

ショートハンド表現からPermissionを構築します

# 例

```julia
Permission("client:books:read,rent")
# Permission("client", ["books"], ["read", "rent"], "", None)

Permission("client::read,rent") # 任意のリソース
# Permission("client", ["*"], ["read", "rent"], "", None)

Permission("admin") # 任意のリソース、任意のアクション
# Permission("admin", ["*"], ["*"], "", None)

Permission("staff:books") # booksに対する任意のアクション
# Permission(staff:books:*:none)

Permission("multi-rental:books,cds:rent")
# Permission("multi-rental", ["books", "cds"], ["rent"], "", None)

Permission("author:*:update:own", "著者は自分のリソースを更新できます")
# Permission("author", ["*"], ["update"], "著者は自分のリソースを更新できます", Own)
```
