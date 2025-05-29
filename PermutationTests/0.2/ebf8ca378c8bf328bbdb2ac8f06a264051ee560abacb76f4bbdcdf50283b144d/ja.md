```julia
function _permTest!(x, y, ns::nsType, stat::Stat, asStat::AsStat;
                    standardized::Bool=false, centered::Bool=false, 
                    nperm::Int = 20000, 
                    fstat::Function = abs,
                    compfunc::Function = >=,
                    switch2rand::Int = Int(1e8),
                    seed::Int = 1234,
                    verbose::Bool = true,
                    cpcd = nothing,
                    kwargs...) where {Stat<:Statistic, AsStat<:Statistic}
```

この関数は最終的に *PermutationsTests.jl* に実装されているすべての **単変量置換検定** を実行します。*正確な* 検定と *近似的* 検定（モンテカルロ）があります。

検定を実行するには、[単変量検定関数](@ref "Univariate tests") を使用してください。この関数は、[独自の検定を作成する](@ref "Create your own test")ためにのみ必要です。

実行される検定に応じて `x` および/または `y` を再定義します。

`ns` 引数については [ns](@ref) を参照してください。

`stat` は [Statistic](@ref) 型のシングルトンまたは、ユーザーが観測された検定統計量と置換された検定統計量の両方を計算するために実装した関数の引数として使用されるこの型のユーザー定義のシングルトンである可能性があります。詳細は [独自の検定を作成する](@ref "Create your own test") を参照してください。

`asStat` は [Statistic](@ref) 型のシングルトンです。これは置換スキームを決定するために使用され、この目的のために内部的に [`genPerms`](@ref) および [`nrPerms`](@ref) に渡されます。

`asStat` は、独自の `stat` 型を宣言した場合の入力データ形式も決定します。この場合、観測された検定統計量と置換された検定統計量を計算するために記述する関数は、次のように `x` および `y` 引数を受け取ります：

`Stat` が [group](@ref "Statistic groups") に属する場合

  * `BivStatistic` : `x`、`y` はそれぞれ $N$ 要素の2つのベクトルであり、二変量統計量が検定されます。`ns` は無視されます。
  * `IndSampStatistic` : $K$ グループがあり、$N=N_1+...+N_K$ の総観測値があります。`y` はすべての観測値を単一のベクトル `[y1;...;yK]` に保持し、`x` は [`membership(::IndSampStatistic)`](@ref) ベクトルです。例えば、$K=2$、$N_1=2$ および $N_2=3$ の場合、`x=[1, 1, 2, 2, 2]` となります。
  * `RepMeasStatistic` : $K$ 測定（*例*、治療）があり、$N$ 被験者があります。`y` は単一のベクトル `[y1;...;yN]` に $K*N$ の観測値を保持し、各ベクトル $y_i$（$i=1...N$）は $K$ の治療における観測値を保持し、`x=collect(1:K*N)` となります（[`membership(::RepMeasStatistic)`](@ref) を参照）。
  * `OneSampStatistic` : $N$ の観測値（*例*、被験者）があり、`y` は $N$ の観測値を保持し、`x=ones(Int, N)` となります（[`membership(::OneSampStatistic)`](@ref) を参照）。

!!! note "Nota Bene"
    すべての場合において、`x` は [`testStatistic`](@ref) 関数を呼び出す前に置換される置換ベクトルとして扱われます。


`length(x)>30` の場合、すべてのケースで近似検定が実行されます。

そうでない場合、

系統的な置換の数が `switch2rand` を超えると、`nperm` のランダム置換（デフォルトは20000）を使用して近似検定が実行されます。

そうでなければ、

正確な検定が実行されます。

`switch2rand` のデフォルトは 1e8 です。すべてのケースで近似検定を実行するには、`switch2rand` を 1 などに設定します。

`stat` が `BivStatistic` の場合、`standardized` または `centered` の kwargs をオプションで使用して、より高速に計算します。例えば [`correlationTest`](@ref) を参照してください。

`seed` はランダム置換を生成するための初期シードです（正確な検定には使用されません）。ランダムシードを使用するには、`seed=0` を渡します。`seed` に任意の自然数を指定すると、検定は再現可能になります。

`fstat` は検定統計量に適用される関数です。デフォルトでは、これは絶対値を取る julia の `abs` 関数であり、したがってゼロの周りに対称的に分布する検定統計量に対して双方向の検定を生成します。右方向の検定を行うには、ここで `identity` を渡します。左方向の検定を行うには、ここで [`flip`](@ref) を渡します。

`compfunc` は観測された統計量を置換された統計量と比較するための関数です。デフォルトの関数は `>=` です。関数のコードを研究していない限り、変更しないでください。

`verbose` が true の場合、検定を実行している間に REPL にいくつかの情報を印刷します。ベンチマークを実行する場合は false に設定します。デフォルトは true です。

`cpcd` および `kwargs...` 引数については、[独自の検定を作成する](@ref "Create your own test") を参照してください。

[UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
x=randn(6)
y=randn(6) 
# x と y の相関の双方向の正確な検定
t8 = _permTest!(μ0(x), μ0(y), length(x), Covariance(), Covariance(); centered=true) 
t8.p
t8.stat
#...

# 左方向の検定を行い、データを標準化する
t8_2 = _permTest!(μ0σ1(x), μ0σ1(y), length(x), Covariance(), Covariance(); 
        standardized=true, fstat=flip) 

# 同じだが近似検定を強制する
t8_3 = _permTest!(μ0σ1(x), μ0σ1(y), length(x), Covariance(), Covariance(); 
        standardized=true, fstat=flip, switch2rand=1) 

# 同じだが5000のランダム置換を使用する
t8_4 = _permTest!(μ0σ1(x), μ0σ1(y), length(x), Covariance(), Covariance(); 
        standardized=true, fstat=flip, switch2rand=1, nperm=5000) 
```

さらに多くの例を確認するには、*src* の github フォルダにある *uniTests_API.jl* ユニットと、*test* の github フォルダにある *runtests.jl* ユニット内の `test_unitests()` 関数を参照してください。
