```julia
function _permMcTest!(x, Y, ns::nsType, stat::Stat, asStat::AsStat;
            standardized::Bool=false, centered::Bool=false, 
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            nperm::Int = 20000, 
            fstat::Function = abs,
            compfunc::Function = >=,
            switch2rand::Int = Int(1e8),
            seed::Int = 1234,
            threaded::Bool = Threads.nthreads()>=4,
            verbose::Bool = true,
            cpcd = nothing) where {Stat<:Statistic, AsStat<:Statistic}
```

この関数は最終的に、*PermutationsTests.jl* に実装されたすべての **多重比較の置換検定** を実行します。*正確* および *近似*（モンテカルロ）の両方です。

テストを実行するには、[多重比較検定関数](@ref "Multiple comparisons tests") を使用してください。この関数は、[独自のテストを作成するため](@ref "Create your own test") のみ必要です。

`stepdown` が true（デフォルト）の場合、テストのステップダウンバージョンが実行されます。この場合、各ステップでの棄却に使用されるのは `fwe`（ファミリー全体の誤り）率です（デフォルト=0.05）。

実行されるテストに応じて `x` および/または `Y` を再記述します。

`ns` 引数については [ns](@ref) を参照してください。

`stat` は [Statistic](@ref) 型のシングルトンであるか、ユーザーが定義したこの型のシングルトンであり、ユーザーが実装した2つの関数の引数として使用され、観測されたテスト統計量と置換されたテスト統計量を計算します。詳細は [独自のテストを作成する](@ref "Create your own test") を参照してください。

!!! warning
    一変量テストとは対照的に、多重比較テストに対しては同等の統計量は不可能です。データが標準化されている場合の `CrossProd()` と、データが中心化されている場合の `Covariance()` のみが相関のようなテストに対して適用されます。

    シングルトンの [Statistic](@ref) 型が使用される場合、他の種類のテストに使用されるべきテスト統計量は `AnovaF_IS()`, `StudentT_IS()`, `AnovaF_RM()`, および `StudentT_1S()` です。


`asStat` は [Statistic](@ref) 型のシングルトンです。これは置換スキームを決定するために使用され、この目的のために [`genPerms`](@ref) および [`nrPerms`](@ref) に渡されます。

`asStat` は、独自の `stat` 型を宣言した場合、入力データ形式も決定します。この場合、観測された統計量と置換された統計量を計算するために記述する2つの関数は、次のように `x` および `Y` 引数を受け取ります。

[グループ](@ref "Statistic groups") に属する `Stat` の場合

  * `BivStatistic` : `x` は $N$ 要素を持つ固定ベクトルで、`Y` は $N$ ベクトルの $M$ ベクトルです。`x` と `Y` の $y_m$ ベクトル間の $M$ の二変量統計量が同時にテストされます。`ns` は無視されます。
  * `IndSampStatistic` : $K$ グループがあり、$N=N_1+...+N_K$ の合計観測値があります。`Y` は $M$ ベクトルで、各ベクトルは $m^{th}$ 仮説のすべての観測値を単一のベクトルに保持します。$m^{th}$ ベクトル $y_m$ は、すべてのグループの観測値を連結したもので、[y[m][1];...;y[m][K]] となります。`x` はすべての仮説に共通の [`membership(::IndSampStatistic)`](@ref) ベクトルです。例えば、$K=2$, $N_1=2$, $N_2=3$ の場合、`x=[1, 1, 2, 2, 2]` です。
  * `RepMeasStatistic` : $K$ 測定（*例*、治療）と $N$ 被験者があります。`Y` は $M$ ベクトルで、各ベクトルは $m^{th}$ 仮説の $K*N$ 観測値を単一のベクトルに保持します。$m^{th}$ ベクトル $y_m$ は `[Y[m][1];...;Y[m][N]]` のようになり、各ベクトル Y[1][n] は $K$ 治療の観測値を保持し、`x=collect(1:K*N)` です（[`membership(::RepMeasStatistic)`](@ref) を参照）。
  * `OneSampStatistic` : $N$ の観測値（*例*、被験者）があります。`Y` は $M$ ベクトルで、各ベクトルは $N$ の観測値を保持し、`x=ones(Int, N)` です（[`membership(::OneSampStatistic)`](@ref) を参照）。

!!! note "Nota Bene"
    すべての場合において、`x` は置換ベクトルとして扱われ、`Y` の各要素に対して [`testStatistic`](@ref) 関数を呼び出す前に置換されます。


オプションのキーワード引数 `switch2rand`, `nperm`, `standardized`, `centered`, `seed`, `fstat`, `compfunc` および `verbose` は、[`_permTest!`](@ref) 関数と同じ意味を持ちます。

`threaded` が true（デフォルト）の場合、仮説、観測値、および置換の数の積が5億を超える場合、関数はマルチスレッドで実行されます。関数に予期しない問題がある場合は、`threaded` を false に設定してみてください。

`cpcd` および `kargs...` 引数については、[独自のテストを作成する](@ref "Create your own test") を参照してください。

[MultcompTest](@ref) 構造体を返します。

実行されたステップの数 $S$ は、返された構造体の `.rejections` フィールドの長さとして取得できます。

*例*

```julia
using PermutationTests
N, M = 8, 100 # 100 仮説, N=8
x=randn(N)
Y=[randn(N) for m=1:M]
# x と Y のすべての M ベクトル間の相関の双方向正確テスト。
T12 = _permMcTest!(x, Y, N, PearsonR(), PearsonR())
T12.p
T12.stat
#...

# データの標準化によるより速い双方向正確テスト
T12_2 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true) 

# 左方向の正確テスト。
T12_3 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true, fstat=flip)

# 上記と同様ですが、近似テストを強制します
T12_4 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true, fstat=flip, switch2rand=1)

# 5000 のランダム置換を使用して同じことを行います
T12_4 = _permMcTest!(μ0σ1(x), [μ0σ1(y) for y in Y], N, CrossProd(), PearsonR(); 
                    standardized=true, fstat=flip, switch2rand=1, nperm=5000)
```

さらに例を確認するには、*src* の github フォルダにある *multcompTests_API.jl* ユニットと、*test* の github フォルダにある *runtests.jl* ユニットの `test_multicompTests()` 関数を参照してください。 ```
