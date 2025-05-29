```
getgeotime(millionyears::Real, unit::Integer; bound=:forward) :: 
	Union{String, Nothing}
getgeotime(millionyears::Real; bound=:forward) :: 
	Vector{Pair{String, String}}
```

特定の `unit` に含まれる与えられた時間瞬間（百万年単位）の地質時代を見つけます。

引数 `unit` は `1`（エオン）、`2`（時代）、`3`（期）、`4`（エポック）、または `5`（年代）でなければなりません； `bound` は `:forward`（デフォルト）または `:backward` でなければなりません。 `unit` が省略された場合、すべての可能な単位の結果がまとめられて返されます。

与えられた時間瞬間を含む地質時代がない場合、`unit` が指定されている場合は `nothing` が返され、または結果は返されるベクターに単に省略されます。

# 例

```jldoctest
julia> getgeotime(39, 3)
"Paleogene"

julia> getgeotime(39)
5-element Vector{Pair{String, String}}:
    "Eon" => "Phanerozoic"
    "Era" => "Cenozoic"
 "Period" => "Paleogene"
  "Epoch" => "Eocene"
    "Age" => "Bartonian"

julia> getgeotime(3900, 3) == nothing
true

julia> getgeotime(3900)
2-element Vector{Pair{String, String}}:
 "Eon" => "Archean"
 "Era" => "Eoarchean"
```
