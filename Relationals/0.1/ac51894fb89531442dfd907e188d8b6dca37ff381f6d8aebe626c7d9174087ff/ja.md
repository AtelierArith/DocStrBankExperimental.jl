```
create(T::Type{<:Relational}; kwargs...)
create(T::Type{<:Relational}, cond::Pair; kwargs...)
create(T::Type{<:Relational}, conds::Union{Tuple,AbstractArray}; kwargs...)
```

型 T の最初のレコードを取得します。

## 例

```julia
# 最初の User レコードを取得します。
julia> create(Manufacturer, :name=>"Sauron Supplies")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# 最初の User レコードを取得します。
julia> create(Manufacturer, (:name=>"Sauron Supplies", :admin_id=>1))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")
```
