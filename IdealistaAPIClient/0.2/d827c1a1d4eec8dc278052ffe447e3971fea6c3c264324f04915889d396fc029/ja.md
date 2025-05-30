```
Bedrooms <: PropertySearchFields
```

寝室特有の検索フィールドを格納する構造体

各フィールドは、Idealista Search APIの有効な寝室検索フィールドを表します。

# コンストラクタ

```julia

Bedrooms(housemates,
         smokePolicy,
         petsPolicy,gayPartners,
         newGender)

Bedrooms(; housemates::Union{<:AbstractString, Nothing}=nothing,
           smokePolicy::Union{<:AbstractString, Nothing}=nothing,
           petsPolicy::Union{<:AbstractString, Nothing}=nothing,
           gayPartners::Union{Bool, Nothing}=nothing,
           newGender::Union{<:AbstractString, Nothing}=nothing)
```

# 例

```jldoctest
julia> Bedrooms("2,4", "disallowed", "disallowed", true, "male")
Bedrooms:
	housemates => 2,4
	smokePolicy => disallowed
	petsPolicy => disallowed
	gayPartners => true
	newGender => male

julia> Bedrooms(housemates="2,4", smokePolicy="disallowed", petsPolicy="disallowed", gayPartners=true, newGender="male")
Bedrooms:
	housemates => 2,4
	smokePolicy => disallowed
	petsPolicy => disallowed
	gayPartners => true
	newGender => male
```
