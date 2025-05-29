```
schema([terms::AbstractVector{<:AbstractTerm}, ]data, hints::Dict{Symbol})
schema(term::AbstractTerm, data, hints::Dict{Symbol})
```

`terms`を使ってモデルを適合させるために必要なすべての不変量を計算します。スキーマは、`Term`をその具体的なインスタンス（`CategoricalTerm`または`ContinuousTerm`のいずれか）にマッピングする`Dict`です。「ヒント」は、オプションで、変数名（`Symbol`として）を用語またはコントラストタイプにマッピングする`Dict`の形で提供できます。変数に対してヒントが提供されていない場合、データ列のデータ型に基づいて適切な用語タイプが推測されます：数値データは連続的であると仮定され、非数値データはカテゴリカルであると仮定されます。

[`StatsModels.Schema`](@ref)を返します。これは、`Term`をその具体的なインスタンス（`ContinuousTerm`または`CategoricalTerm`）にマッピングする`Dict`のラッパーです。

# 例

```jldoctest 1
julia> using StableRNGs; rng = StableRNG(1);

julia> d = (x=sample(rng, [:a, :b, :c], 10), y=rand(rng, 10));

julia> ts = [Term(:x), Term(:y)];

julia> schema(ts, d)
StatsModels.Schema with 2 entries:
  x => x
  y => y

julia> schema(ts, d, Dict(:x => HelmertCoding()))
StatsModels.Schema with 2 entries:
  x => x
  y => y

julia> schema(term(:y), d, Dict(:y => CategoricalTerm))
StatsModels.Schema with 1 entry:
  y => y
```

具体的な`ContinuousTerm`と`CategoricalTerm`、そして型指定のない`Term`は、コンテナ内では同じように表示されますが、単独で表示されると異なります：

```jldoctest 1
julia> sch = schema(ts, d)
StatsModels.Schema with 2 entries:
  x => x
  y => y

julia> term(:x)
x(unknown)

julia> sch[term(:x)]
x(DummyCoding:3→2)

julia> sch[term(:y)]
y(continuous)
```
