```
Search <: SearchFields
```

Idealista Search APIの基本的な（プロパティタイプ特有でない）検索フィールドを格納する構造体

各フィールドは、Idealista Search APIの有効な基本検索フィールドを表します。国、操作、プロパティタイプ、そして中心 + 距離または中心 + locationIdは必須です。

# コンストラクタ

```julia

Search(country,
       operation,
       propertyType,
       center,
       maxItems,
       numPage,
       maxPrice,
       minPrice,
       sinceDate,
       orderg,
       sort,
       adIds,
       hasMultimedia,
       distance,
       locationId,
       locale)

Search(; country::String,
         operation::String,
         propertyType::String,
         center::String,
         maxItems::Union{<:Int, Nothing}=nothing,
         numPage::Union{<:Int, Nothing}=nothing,
         maxPrice::Union{<:Number, Nothing}=nothing,
         minPrice::Union{<:Number, Nothing}=nothing,
         sinceDate::Union{<:AbstractString, Nothing}=nothing,
         order::Union{<:AbstractString, Nothing}=nothing,
         sort::Union{<:AbstractString, Nothing}=nothing,
         adIds::Union{<:Int, Nothing}=nothing,
         hasMultimedia::Union{Bool, Nothing}=nothing,
         distance::Union{<:Int, Nothing}=nothing,
         locationId::Union{<:AbstractString, Nothing}=nothing,
         locale::String)
```

# 例

```jldoctest
julia> Search("es", "sale", "homes", "42.0,-3.7",  nothing, nothing, nothing, nothing, nothing, nothing, nothing, nothing, nothing, 15000,  nothing, "ca")
Search:
	country => es
	operation => sale
	propertyType => homes
	center => 42.0,-3.7
	maxItems => nothing
	numPage => nothing
	maxPrice => nothing
	minPrice => nothing
	sinceDate => nothing
	order => nothing
	sort => nothing
	adIds => nothing
	hasMultimedia => nothing
	distance => 15000
	locationId => nothing
	locale => ca

julia> Search(country="it", operation="sale", propertyType="homes", center="42.0,-3.7", locale="es", distance=15000)
Search:
	country => it
	operation => sale
	propertyType => homes
	center => 42.0,-3.7
	maxItems => nothing
	numPage => nothing
	maxPrice => nothing
	minPrice => nothing
	sinceDate => nothing
	order => nothing
	sort => nothing
	adIds => nothing
	hasMultimedia => nothing
	distance => 15000
	locationId => nothing
	locale => es

julia> Search("it", "sale", "homes", "42.0,-3.7", locale="es", distance=15000)
Search:
	country => it
	operation => sale
	propertyType => homes
	center => 42.0,-3.7
	maxItems => nothing
	numPage => nothing
	maxPrice => nothing
	minPrice => nothing
	sinceDate => nothing
	order => nothing
	sort => nothing
	adIds => nothing
	hasMultimedia => nothing
	distance => 15000
	locationId => nothing
	locale => es
```
