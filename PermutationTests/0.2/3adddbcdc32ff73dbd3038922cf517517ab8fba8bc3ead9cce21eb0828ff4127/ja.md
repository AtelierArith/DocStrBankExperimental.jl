```julia
signTest(𝐲::Union{BitVector, Vector{Bool}};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where TestDir <: TestDirection =

```

データの置換による単変量 [符号検定](https://en.wikipedia.org/wiki/Sign_test)。帰無仮説は次の形を持ちます。

$$
H_0: E(true)=E(false)
$$

,

ここで、$E(true)$ と $E(false)$ はそれぞれ真と偽の出現回数の期待値です。

`y` は $N$ 個のブール値のベクトルです。

オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests")を参照してください。

*方向性検定*

  * 右方向の検定の場合、$E(true)$ は $E(false)$ を超えることが期待されます。逆の場合、検定は p 値が 0.5 より高くなります。
  * 左方向の検定の場合、$E(false)$ は $E(true)$ を超えることが期待されます。逆の場合、検定は p 値が 0.5 より高くなります。

正確な検定のための置換スキームと置換の数: [`studentTest1S`](@ref) に従います。

単変量符号検定の有意性は、二項分布を使用してはるかに効率的に得ることができます。この置換検定は単変量の場合には全く役に立たないため、しかし、その多重比較バージョンはデータの置換によって家族全体の誤り率を制御することを可能にします。

**多重比較バージョン**

[`signMcTest`](@ref)

[UniTest](@ref) 構造体を返します。

*例*

```julia
using PermutationTests
N=20; # 観測数
y = rand(Bool, N); # 例えばいくつかのランダムなガウスデータ
t = signTest(y) # デフォルトでは検定は双方向です

tR = signTest(y; direction=Right()) # 右方向の検定
tL = signTest(y; direction=Left()) # 左方向の検定
# 5000回のランダム置換で近似検定を強制
tapprox = signTest(y; switch2rand=1, nperm=5000) 
```
