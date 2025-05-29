```julia
function correlationMcTest(x::UniData, Y::UniDataVec;
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)), 
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true, 
            #
            standardized::Bool = false,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection
```

データの置換による複数比較 [ピアソンの積率相関検定](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Testing_using_Student's_t-distribution)。

$$
M
$$

個の相関検定を同時に実行します。入力データは固定ベクトル `x` と $M$ ベクトルを `Y` として与えられ、$M$ 個のベクトル $y_1,...,y_M$ から成ります。

`x` と `Y` のすべてのベクトルは同じ長さでなければなりません。

$$
M
$$

個の帰無仮説は次の形を持ちます。

$$
H_0(m):r_{(x, y_m)}=0, \quad m=1...M
$$

、

ここで $r_{x,y_m}$ はベクトル `x` と `Y` の $m^{th}$ ベクトルとの間のピアソン相関係数です。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` については、[こちら](@ref "Common kwargs for multiple comparisons tests")を参照してください。

`standardized` が true の場合、`x` と `Y` のすべてのベクトルは標準化されていると仮定されます（平均0、標準偏差1）。標準化された入力データを使用すると、交差積が実際には相関であるため、テストをより速く実行できます。`standardized` が false の場合、データはより速いテストを実行するために標準化されます。

*方向性テスト、置換スキームおよび正確なテストのための置換回数:* *単変量バージョン* [`correlationTest`](@ref) に従います。

*エイリアス:* `rMcTest`、[`trendMcTest`](@ref)

[MultcompTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
N=10; # 観測数
M=100; # テスト数
x=randn(N);
Y=[randn(N) for i=1:M];
t=rMcTest(x, Y) # 双方向テスト
```

```julia
tR=rMcTest(x, Y; direction=Right()) # 右方向テスト
tL=McTest(x, Y; direction=Left()) # 左方向テスト
tMC=rMcTest(x, Y; switch2rand=1) # モンテカルロテストを強制
# モンテカルロテストを強制し、50Kの置換を実行
t5K=rMcTest(x, Y; switch2rand=1, nperm= 50_000) 
tnoSD=rMcTest(x, Y; stepdown=false) # ステップダウンを行わない
tnoMT=rMcTest(x, Y; threaded=false) # マルチスレッドで実行しない
t001=rMcTest(x, Y; fwe=0.01) # ステップダウンが0.05ではなく0.01レベルで拒否
```

**類似のテスト**

[correlationTest](@ref) を参照してください。
