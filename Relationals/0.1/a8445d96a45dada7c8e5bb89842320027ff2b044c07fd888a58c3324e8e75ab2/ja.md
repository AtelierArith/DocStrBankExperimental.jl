```
first(T::Type{<:Relational}; kwargs...)
first(T::Type{<:Relational}, cond::Int; kwargs...)
first(T::Type{<:Relational}, cond::String; kwargs...)
first(T::Type{<:Relational}, cond::Pair; kwargs...)
first(T::Type{<:Relational}, cond::UUID; kwargs...)
first(T::Type{<:Relational}, conds::Union{Tuple,AbstractArray}; kwargs...)
```

型Tの最初のレコードを取得します。

## 例

```julia
# 最初のUserレコードを取得します。
julia> first(User)
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# id=1の最初のUserレコードを取得します。
julia> first(User, 1)
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# "uuid IS NOT NULL"の条件で最初のUserレコードを取得します。
> first(User, "uuid IS NOT NULL")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# last_name="Baggins"の条件で最初のUserレコードを取得します。
> first(User, :last_name=>"Baggins")
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# first_name="Bilbo"の条件で最初のUserレコードを取得します。
> first(User, :first_name=>:Bilbo)
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# uuid="c6dacd6f-0023-4aba-bf24-374f4042fc47"の条件で最初のUserレコードを取得します。
> first(User, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# id=1かつuuid="c6dacd6f-0023-4aba-bf24-374f4042fc47"の条件で最初のUserレコードを取得します。
> first(User, (:id=>1, :uuid=>UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47")))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# last_name="Baggins"かつuuidがnullでない条件で最初のUserレコードを取得します。
> first(User, (:last_name=>:Baggins, "uuid IS NOT NULL"))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# last_name="Baggins"かつfirst_nameが"Frodo"または"Bilbo"の条件で最初のUserレコードを取得します。
> first(User, (:last_name=>:Baggins, :first_name=>["Frodo", "Bilbo"]))
User(1, UUID("c6dacd6f-0023-4aba-bf24-374f4042fc47"), "Bilbo", "Baggins")

# first_name="Frodo"かつ(id > 1 OR last_name="Baggins")の条件で最初のUserレコードを取得します。
> first(User, (:first_name=>:Frodo, "id > 1 OR last_name='Baggins'"))
User(2, UUID("0bb0cdc4-b1d3-43ac-93ad-693a94fc9ceb"), "Frodo", "Baggins")
```
