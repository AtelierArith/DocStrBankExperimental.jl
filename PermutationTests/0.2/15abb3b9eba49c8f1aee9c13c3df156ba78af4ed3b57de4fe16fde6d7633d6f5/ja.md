```julia
function studentTest1S(𝐲::UniData;
            refmean::Realo = nothing,
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where TestDir <: TestDirection =
```

データの置換による単変量 [一標本t検定](https://en.wikipedia.org/wiki/Student's_t-test#One-sample_t-test)。帰無仮説は次の形を持ちます。

$$
H_0: μ=μ_0
$$

,

ここで $μ$ は観測値の平均で、$μ_0$ は参照母集団の平均です。

`refmean` は上記の参照平均 ($μ_0$) です。デフォルトは $0$ で、これはほとんどの検定で使用される値です。

オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests")を参照してください。

*方向性検定*

  * 右方向性検定の場合、$μ$ は $μ_0$ を超えることが期待されます。逆の場合、検定は p 値が 0.5 より高くなります。
  * 左方向性検定の場合、$μ_0$ は $μ$ を超えることが期待されます。逆の場合、検定は p 値が 0.5 より高くなります。

*置換スキーム:* 一標本t検定は、2つの繰り返し測定のt検定に相当し、その差の平均が一標本t検定によって検定されます。帰無仮説の下では、2つの測定の順序には意味がありません。交換可能性スキームは、$N$ の観測単位における2つの測定を再配置することから成ります。一標本t検定の場合、これは観測値を観測された符号と反転した符号で考慮することに相当します。

*正確な検定のための置換の数:* `y` の $N$ の観測における2つの測定を再配置する方法は $2^N$ 通りあります。一標本t検定の場合、これは観測値の符号の可能な構成の数です。

**エイリアス:** `tTest1S` 

多重比較バージョン: [`studentMcTest1S`](@ref)

[UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
N=20 # 観測の数
y = randn(N) # 例としてのランダムなガウスデータ
t = tTest1S(y) # H0: μ(y)=0 を検定します。デフォルトでは検定は双方向です

t = tTest1S(y; refmean=1.) # H0: μ(y)=1 を検定
tR = tTest1S(y; direction=Right()) # 右方向性検定
tL = tTest1S(y; direction=Left()) # 左方向性検定
# 5000回のランダム置換で近似検定を強制
tapprox = tTest1S(y; switch2rand=1, nperm=5000) 
```

**類似の検定**

通常、入力データは実数ですが、整数またはブール型でも構いません。もし `y` がブール値のベクトルまたは二項データ（0と1のみ）のベクトルである場合、この関数は実際には [符号検定](https://en.wikipedia.org/wiki/Sign_test) の置換ベースのバージョンを実行します。ブール入力の場合は、[signTest](@ref) 関数を使用してください。

2つの繰り返し測定の差のベクトルをデータ入力として渡すと、この関数は繰り返し測定のためのスチューデントのt検定を実行します。そのような検定が必要な場合は、[`studentTestRM`](@ref) エイリアスを使用することをお勧めします。
