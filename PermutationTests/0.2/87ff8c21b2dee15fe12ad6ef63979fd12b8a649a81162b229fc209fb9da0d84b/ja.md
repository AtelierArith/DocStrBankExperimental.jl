```julia
function correlationTest(x::UniData, y::UniData;
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8), 
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            standardized::Bool = false, 
            centerd::Bool = false,
            verbose::Bool = true) where TestDir <: TestDirection
```

データの置換による単変量 [ピアソン積率相関検定](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient#Testing_using_Student's_t-distribution)。帰無仮説は次の形を持ちます。

$$
H_0: r_{(x,y)}=0
$$

,

ここで $r_{(x,y)}$ は2つの入力データベクトル `x` と `y` の相関であり、通常は実数で、どちらも $N$ の観測値を持ちます。

オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests")を参照してください。

`standardized` が true の場合、`x` と `y` は標準化されていると仮定されます（平均0、標準偏差1）。入力データが標準化されている場合、検定は同じp値を提供しますが、この場合、クロスプロダクトはピアソン *r* 統計量に相当するため、より高速に実行できます（[統計量](@ref)を参照）。

`centered` が true の場合、`x` と `y` は中心化されていると仮定されます（平均0）。検定は同じp値を提供しますが、検定が双方向である場合、同等の統計量である共分散は、Nで割ったクロスプロダクトに簡略化されるため、より高速に実行できます。

`standardized` も `centered` も true でない場合、データは標準化され、クロスプロダクトをテスト統計量として使用してより高速な検定が実行されます。

*方向性検定*

  * 右方向の検定では、相関は正であると期待されます。負の相関はp値が0.5より高くなります。
  * 左方向の検定では、相関は負であると期待されます。正の相関はp値が0.5より高くなります。

*置換スキーム:* 帰無仮説の下では、データ入力ベクトル内の観測値の位置には意味がありません。交換可能性スキームは、ベクトル `x` またはベクトル `y` の観測値をシャッフルすることから成ります。*PermutationTests.jl* は `x` の観測値をシャッフルします。

*正確な検定のための置換の数:* `x` の $N$ 観測値を再配置する方法は $N!$ 通りあります。

*エイリアス:* `rTest!`、[`trendTest!`](@ref)

*多重比較バージョン:* [correlationMcTest!](@ref)

[UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
N=10 # 観測値の数
x, y = randn(N), randn(N) # 例としてのランダムなガウスデータ
t = rTest(x, y) # デフォルトでは検定は双方向
```

```@julia
tR = rTest(x, y; direction=Right()) # 右方向の検定
tL = rTest(x, y; direction=Left()) # 左方向の検定
# 5000回のランダム置換で近似検定を強制
tapprox = rTest(x, y; switch2rand=1, nperm=5000) 
```

**類似の検定**

通常、入力データは実数ですが、整数またはブール型のデータでも構いません。`x` または `y` がブール型のベクトルまたは二項データのベクトル（0と1のみ）である場合、この関数は実際には [ポイントバイセリアル相関検定](https://en.wikipedia.org/wiki/Point-biserial_correlation_coefficient) の置換ベースのバージョンを実行します。ただし、前述のリンクに示されているように、ポイントバイセリアル相関検定は独立サンプルのt検定に相当するため、独立サンプルのt検定を使用して検定することができ、相関検定に比べてはるかに少ない置換で済みます（以下の例を参照）。専用の関数 [`pointBiSerialTest`](@ref) が利用可能で、これは [`studentTestIS`](@ref) のエイリアスであり、相関またはt検定統計量を使用して検定を実行する選択肢を提供します。

`x` または `y` が *トレンド* を表す場合、例えば `[1, 2,...N]` で与えられる線形トレンドの場合、置換ベースのトレンド相関検定を取得し、`y` を `x` に対して回帰する任意のタイプのフィットをテストするために使用できます - [trendTest](@ref) を参照してください。

もし `y` が遅延 $l$ の `x` のシフトバージョンである場合、この関数は *遅延 $l$ における自己相関の有意性* をテストします。ページ [Create your own test](@ref) を参照してください。

*例*

```julia
# ポイントバイセリアル相関検定
using PermutationTests
N=10 # 観測値の数
x=[0, 0, 0, 0, 1, 1, 1, 1, 1, 1]
y = rand(N)
t = rTest(x, y) 

# 全く同じ検定は独立サンプルのt検定として得られますが、
# 後者は正確な検定のために210回の置換しか必要とせず、
# 前者は3628800回の置換を必要とするため、はるかに高速です。
# 専用の関数で利用可能です
t2=pointBiSerialTest(y, [4, 6])
println(t.p ≈ t2.p ? "OK" : "error")
```
