```julia
function allPerms(stat::BivStatistic, ns::Int) 

function allPerms(stat::IndSampStatistic, ns::Vector{Int})

function allPerms(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int})

function allPerms(stat::OneSampStatistic, ns::Int)

```

与えられた [group](@ref "Statistic groups") の単一の `stat` に対する検定統計量の系統的な全置換の総数（正確な検定）。

`ns` 引数については [ns](@ref) を参照してください。

$$
N
$$

の観測値と $K$ のグループ/測定がある正確な検定の場合、系統的な置換の総数は次のとおりです。

  * `stat` が `BivStatistic` の場合 :$\quad N!$
  * `stat` が `IndSampStatistic` の場合 : $\quad \frac{N!}{N_1! \cdot \ldots \cdot N_K!}$
  * `stat` が `RepMeasStatistic` の場合 : $\quad K!^N$
  * `stat` が `OneSampStatistic` の場合 : $\quad 2^N$

正確な検定のためにリストされる実際の置換の数である非冗長置換の数については [`nrPerms`](@ref) を参照してください。

*例*

```julia
# 独立サンプルの1-way ANOVAのための可能な置換の総数 
# バランスの取れた3つのグループで合計18の観測値を持つ検定。
allPerms(AnovaF_IS(), [6, 6, 6]) # -> 17153136

# 12の観測値を持つ相関検定のための可能な置換の総数。
allPerms(PearsonR(), 12) # -> 479001600
```
