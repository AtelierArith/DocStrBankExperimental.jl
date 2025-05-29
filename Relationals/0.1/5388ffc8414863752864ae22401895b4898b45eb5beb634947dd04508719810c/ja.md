```
updatemany(T::Type{<:Relational}, key::Union{Int,UUID}, value::Pair; kwargs...)
updatemany(T::Type{<:Relational}, key::Union{Int,UUID}, values::Union{Tuple,AbstractArray}; kwargs...)
```

ユニークキー（Int型の:idまたはUUID型の:uuid）に一致するレコードをvalue(s)で更新します。

## 例

```julia
# 最初のUserレコードを取得します。
julia> update(Manufacturer, 1, :name=>"Sauron Supplies")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# 最初のUserレコードを取得します。
julia> update(Manufacturer, 1, (:name=>"Sauron Supplies", :admin_id=>1))
User(1, update("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")
```
