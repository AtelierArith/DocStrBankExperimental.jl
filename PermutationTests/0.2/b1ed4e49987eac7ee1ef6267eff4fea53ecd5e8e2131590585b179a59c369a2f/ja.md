```julia
function signMcTest(Y::Union{AbstractVector{BitVector}, AbstractVector{Vector{Bool}}};
            direction::TestDir = Both(),
            switch2rand::Int= max(Int(1e8) ÷ length(𝐘), Int(1e4)),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            #
            stepdown::Bool = true,
            fwe::Float64 = 0.05,
            threaded::Bool = Threads.nthreads()>=4) where TestDir <: TestDirection

```

データの置換による複数比較 [符号検定](https://en.wikipedia.org/wiki/Sign_test)。

$$
M
$$

個の符号検定を同時に実行します。帰無仮説は次の形を持ちます。

$$
H_0(m): E_m(true)=E_m(false), \quad m=1...M
$$

、

ここで、$E_m(true)$ と $E_m(false)$ はそれぞれ $m^{th}$ 仮説における真の出現数と偽の出現数の期待値です。

`Y` は各 $N$ のブール値を保持する $M$ 個のベクトルのベクトルです。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` の詳細は [こちら](@ref "Common kwargs for multiple comparisons tests") を参照してください。

*方向性検定、置換スキームおよび正確な検定のための置換回数:* *単変量バージョン* [`signTest`](@ref) に従います。

[MultcompTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
N=20; # 観測数
M=100; # 仮説の数
Y = [rand(Bool, N) for m=1:M]; # 例としてのいくつかのランダムなガウスデータ
t = signMcTest(Y) # デフォルトでは検定は双方向です

tR = signMcTest(Y; direction=Right()) # 右方向の検定
tL = signMcTest(Y; direction=Left()) # 左方向の検定

# 5000回のランダム置換で近似検定を強制
tapprox = signMcTest(Y; switch2rand=1, nperm=5000) 
```
