```julia
function studentMcTest1S(Y::UniDataVec;
            refmean::Realo = nothing,
            direction::TestDir = Both(),
            switch2rand::Int = max(Int(1e8) ÷ length(𝐘), Int(1e4)),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection 
```

データの置換による複数比較 [一標本t検定](https://en.wikipedia.org/wiki/Student's_t-test#One-sample_t-test)。

$$
M
$$

個の一標本t検定を同時に実行します。帰無仮説は次の形を持ちます。

$$
H_0(m): μ_m=μ_0, \quad m=1...M
$$

、

ここで $μ_m$ は $m^{th}$ 仮説の観測値の平均であり、$μ_{0}$ は参照母集団の平均です。

`refmean` は上記の参照平均 ($μ_0$) です。デフォルトは `0.0` で、ほとんどの状況で必要な値です。

`Y` は $M$ 個のベクトルを持つベクトルで、それぞれが $N$ 個の観測値を保持し、その平均が $μ_0$ と比較されます。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` の詳細は [こちら](@ref "Common kwargs for multiple comparisons tests") を参照してください。

*方向性検定、置換スキームおよび正確な検定のための置換回数:* *単変量バージョン* [`studentTest1S`](@ref) に従います。

*エイリアス:* `tTest1S`

[MultcompTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
N=20 # 観測数
M=100 # 仮説数
y = [randn(N) for m=1:M]; # 例としてのランダムなガウスデータ
t = tMcTest1S(Y) # デフォルトでは検定は双方向です

tR = tMcTest1S(Y; direction=Right()) # 右方向の検定
tL = tMcTest1S(Y; direction=Left()) # 左方向の検定

# 5000回のランダム置換で近似検定を強制
tapprox = tMcTest1S(Y; switch2rand=1, nperm=5000) 

# H0m: μ(ym)=1.5を検定: 期待される平均が0.0であるため、すべて棄却されます
t1 = tMcTest1S(Y; refmean=1.5) 
```

**類似の検定**

[`studentTest1S`](@ref) を参照してください。
