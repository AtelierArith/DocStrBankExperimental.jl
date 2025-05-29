```julia
function nrPerms(stat::Union{BivStatistic, OneSampStatistic}, ns::Int, total, 
                direction::TestDir, design::Assign=Balanced()) 

function nrPerms(stat::IndSampStatistic, ns::Vector{Int}, total, 
                direction::TestDir, design::Assign)

function nrPerms(stat::RepMeasStatistic, ns::@NamedTuple{n::Int, k::Int}, total, 
                direction::TestDir, design::Assign=Balanced())
                
    where {TestDir<: TestDirection, Assign <: Assignment}

```

非冗長な系統的順列の数。これは、正確なテストのためにリストされる実際の順列の数です。

テストの方向とデザインによっては、冗長な順列、すなわち同じテスト統計を生成する順列が存在する場合があります。これらの順列は排除され、テストが速くなります。

`stat`は、単一のテスト統計として与えられるテストで使用されるテスト統計です。これは、テスト統計の1つの[グループ](@ref "Statistic groups")に属します。

`ns`引数については[ns](@ref)を参照してください。

`total`は、系統的順列の総数です。エラーを避けるために、[`allPerms`](@ref)関数の結果として与えるべきです。

`direction`は、[TestDirection](@ref)型の単一の値です。

`design`は、[Assignment](@ref)型の単一の値です。エラーを避けるために、引数`design`として[`assignment`](@ref)の結果を使用してください。

`stat`が`IndSampStatistic`でバランスの取れたデザインの場合、非冗長な順列は$\frac{total}{K!}$であり、$K$はグループの数です。

`stat`が`RepMeasStatistic`で双方向テストの場合、非冗長な順列は$\frac{total}{K!}$であり、$K$は測定の数です。

`stat`が`BivStatistic`または`OneSampStatistic`の場合は`total`を返します。つまり、冗長性はありません。

冗長な順列の排除は、順列テストのソフトウェアパッケージではほとんど実装されていないことに注意してください。

*例*

```julia
using PermutationTests
# 独立サンプルの1-way ANOVAテストのための可能な順列の数
# バランスの取れた3つのグループで合計18の観察があります。
ns=[6, 6, 6]
total=allPerms(AnovaF_IS(), ns) # -> 17153136
# 実際にテストを実行するためにリストされる非冗長な順列の数。
design=assignment(AnovaF_IS(), ns)
nrPerms(AnovaF_IS(), ns, total, Both(), design) # -> 2858856
```
