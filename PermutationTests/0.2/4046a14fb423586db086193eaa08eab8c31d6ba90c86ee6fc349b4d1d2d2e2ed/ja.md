```julia
function genPerms(stat::BivStatistic, x::UniData, 
            ns::Int, direction::TestDir, design::Assign) 
    
function genPerms(stat::IndSampStatistic, x::UniData, 
            ns::Vector{Int}, direction::TestDir, design::Assign)
                
function genPerms(stat::RepMeasStatistic, x::UniData, 
            ns::@NamedTuple{n::Int, k::Int}, direction::TestDir, design::Assign)
            
function genPerms(stat::OneSampStatistic, x::UniData, 
            ns::Int, direction::TestDir, design::Assign)

    where {TestDir<: TestDirection, Assign <: Assignment}
```

テスト統計量 `stat` に使用される順列スキームに従って、すべての可能な（系統的な）順列に対する *遅延* イテレータを生成します。`stat` は [Statistic](@ref) 型のシングルトンとして与えられます。

*PermutationsTests.jl* におけるデータの順列は常に遅延イテレータによって取得されるため、順列は物理的にリストされることはありません。これは、このパッケージが高速であり、少ないメモリを割り当てる主な理由の一つです。

パッケージの一般的な使用にはこれらの関数は必要ありませんが、[自分のテストを作成する](@ref "Create your own test") ことを希望する場合は、これらを知っておく必要があります。

テスト統計量 `stat` が属する各 [group](@ref "Statistic groups") に対して順列スキームが存在します。

`x` は [`membership`](@ref) ベクトルです。

`ns` 引数については [ns](@ref) を参照してください。

`direction` は [TestDirection](@ref) 型のシングルトンです。

`design` は [Assignment](@ref) 型のシングルトンです。エラーを避けるために、[`assignment`](@ref) の結果を引数 `design` として使用してください。

`stat` が `BivStatistic` (*例*: `PearsonR()`) の場合、イテレーションはベクトル `x` の $N$ 要素の $N!$ の可能な再配置を展開し、引数 `ns` は無視されます。この場合、`x` はトレンド（例: 線形トレンドのための [1,...,N]）または相関/トレンドテストのために順列化される変数です。

`stat` が `IndSampStatistic` (*例*: `AnovaF_IS()`) の場合、イテレーションは $K$ グループ内の $N$ 要素の $\frac{N!}{N_1 \cdot \ldots \cdot N_K}$ の可能な配置を展開します。この場合、`x` は無視され、`ns` は K グループの数（すなわち [N1,...,Nk]）を保持するベクトルです。このスキームでは、デザインがバランスが取れている場合、すなわち `ns` のすべての要素が等しい場合、一部の順列は冗長です。詳細は [`nrPerms`](@ref) を参照してください。

`stat` が `RepMeasStatistic` (*例*: `AnovaF_RM()`) の場合、イテレーションはすべての $N$ 観察（例: 被験者）における $K$ 測定（例: 処置）の $(K!)^N$ の再配置を展開します。この場合、`x` は無視され、`ns` は形式 `(n=N, k=K)` の [named tuple](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types) です。このスキームでは、テストが双方向の場合、一部の順列は冗長です。詳細は [`nrPerms`](@ref) を参照してください。

`stat` が `OneSampStatistic` (*例*: `StudentT_1S()`) の場合、イテレーションは $2^N$ の符号反転パターンを展開します。この場合、`x` は無視され、`ns=N` であり、$N$ は観察の数です。

!!! note "nota bene"
    `OneSampStatistic` グループに属する `stat` のみの場合、イテレータは配列ではなくタプルを生成します（以下の例を参照）。


!!! tip "keep in mind"
    順列スキームに関係なく、最初に生成されるイテレーションは常に観察されたデータの「順列」に対応します（つまり、実際にデータを順列化しない唯一の順列です）。


*例*

```julia
using PermutationsTests

x=membership(PearsonR(), 3) # -> [1, 2, 3]
# 観察は常に自然な順序 1, 2,... でリストされます
Pr = genPerms(PearsonR(), x, 0, Both(), Balanced()) 
collect(Pr) # イテレーションを物理的にリストする
# 6 = 3! 要素 [1, 2, 3]...[3, 2, 1] を生成します
# ここで整数は x 内の観察の順序を表します

PfIS = genPerms(AnovaF_IS(), Int[], [2, 3], Both(), Unbalanced()) 
collect(PfIS)
# 10 = 5!/2!3! 要素 [1, 1, 2, 2, 2]...[2, 2, 2, 1, 1] を生成します
# ここで整数はデータベクトル `y` 内の対応する観察が属する順列化されたグループを表します。詳細は `_permTest!` を参照してください。
# デザインがバランスが取れていてテストが双方向の場合、 
# 順列の 1/k! のみが保持されます。したがって 
PfIS_ = genPerms(AnovaF_IS(), Int[], [2, 2], Both(), Balanced()) 
collect(PfIS_) 
# 3 = (4!/2!2!)/2! 要素 [1, 1, 2, 2], [1, 2, 2, 1] および [2, 1, 2, 1] を生成します

PfRM = genPerms(AnovaF_RM(), Int[], (n=2, k=3), Right(), Balanced()) 
collect(PfRM)
# 36 = (k!)^n 要素 [1, 2, 3, 4, 5, 6], [1, 3, 2, 4, 5, 6], 
# ..., [3, 2, 1, 6, 5, 4] を生成します
# ここで整数はデータベクトル `y` 内の対応する観察が属する各被験者の処置を表します。詳細は `_permTest!` を参照してください。
# テストが双方向の場合、 
# 順列の 1/k! のみが保持されます。したがって 
PfRM_ = genPerms(AnovaF_RM(), Int[], (n=2, k=3), Both(), Balanced()) 
collect(PfRM_)
# 6 = (k!)^n / 要素 [1, 2, 3, 4, 5, 6], [1, 3, 2, 4, 5, 6], 
# ..., [3, 2, 1, 4, 5, 6] を生成します

Pt1S = genPerms(StudentT_1S(), Int[], 3, Both(), Balanced())
collect(Pt1S)
# 8=2^3 要素 (1, 1, 1), (-1, 1, 1), (1, -1, 1), (-1, -1, 1), 
#..., (-1, -1, -1) を生成します 
# ここで整数は各データ順列に対して各観察に適用される符号を表します。 
# OneSampStatistic のみの場合、イテレータは配列ではなくタプルを生成することに注意してください。
```
