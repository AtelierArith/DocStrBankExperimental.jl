```julia
# METHOD (3)
function studentMcTestIS(X::UniDataVec, Y::UniDataVec; <same kwargs>)
```

**METHOD (1)**

データの置換による複数比較 [独立したサンプルのためのスチューデントのt検定](https://en.wikipedia.org/wiki/Student's_t-test#Independent_(unpaired)_samples)。

$$
M
$$

個の t 検定を同時に実行します。2つのグループそれぞれに $N=N_1+N_2$ の観測値がある $M$ 個の仮説が与えられた場合、$M$ 個の帰無仮説は次の形になります。

$$
H_0(m): μ_{m1}=μ_{m2}, \quad m=1...M
$$

、

ここで $μ_{m1}$ と $μ_{m2}$ はそれぞれ $m^{th}$ 仮説に対するグループ 1 とグループ 2 の平均です。

双方向検定の場合、この t 検定は2つの独立したサンプルに対する1-way ANOVAに相当します。しかし、ANOVAとは異なり、方向性を持つことができます。

`ns` はグループの数を保持する整数のベクトル $N_1, N_2$ です（以下の例を参照）。

オプションのキーワード引数 `direction`, `switch2rand`, `nperm`, `seed`, `verbose`, `stepdown`, `fwe` および `threaded` については [こちら](@ref "Common kwargs for multiple comparisons tests") を参照してください。

`asPearson` が true（デフォルト）である場合、テストはピアソン相関検定の同等のバージョンとして実行されます。これは一般的に複数比較検定にとって有利であり、特に近似的な場合（[ベンチマーク](@ref "Benchmarks")を参照）において有利です。正確な検定のために最良のパフォーマンスを求める場合は、`asPearson` を true と false に設定してテストの速度をベンチマークし、どのバージョンがデータに対して速いかを確認してください。

!!! note "nota"
    `asPearson` が true の場合、テスト結果の `.stat` フィールドは実際には `CrossProd()` になります。データはテストを実行する前に標準化されるためです。 [`correlationTest`](@ref) を参照してください。


*方向性検定、置換スキームおよび正確な検定のための置換数:* *単変量バージョン* [`studentTestIS`](@ref) に従って

*エイリアス:* `tTestMcIS`, [`pointBiSerialMcTest`](@ref)

[MultcompTest](@ref) 構造体を返します。

**METHOD (2)**

方法 (1) と同様ですが、入力データ `Yvec` は任意の長さのベクトルの $M$ ペアを含むベクトルであり、グループ 1 とグループ 2 に対する $m^{th}$ 仮説に対応するデータを自然な順序で保持します。

**METHOD (3)**

方法 (1) と同様ですが、入力データ `X` と `Y` はそれぞれ $M$ 個の観測値のベクトルを保持し、`X` はグループ 1 のデータに、`Y` はグループ 2 のデータに対応します。`X` の $M$ 個のベクトルはすべて同じ長さ ($N_1$) でなければならず、`Y` の $M$ 個のベクトルも同様です ($N_2$)。

*例*

```julia
# (1)
using PermutationTests
M=100 # 仮説の数
ns=[4, 5] # グループ 1 とグループ 2 の観測数 (N1 と N2)
N=sum(ns) # 観測の総数
Yvec = [[randn(n) for n in ns] for m=1:M]; # 例としてのいくつかのランダムなガウスデータ
Y=[vcat(yvec...) for yvec in Yvec];
t = tMcTestIS(Y, ns) # デフォルトではテストは双方向です

# 10000回のランダム置換で近似テストを強制
tapprox = tMcTestIS(Y, ns; switch2rand=1, nperm=10000) 
tR=tMcTestIS(Y, ns; direction=Right()) # 右方向の検定
tL=tMcTestIS(Y, ns; direction=Left()) # 左方向の検定

# 双方向検定では、t は独立したサンプルのための1-way ANOVAに相当します
tanova= fMcTestIS(Y, ns) 
println(sum(abs.(t.p - tanova.p)) ≈ 0. ? "OK" : "error")

# CrossProd テスト統計を使用して実行しないでください
tcor = tMcTestIS(Y, ns; asPearson=false) 

# 方法 (2) では、入力データのフォーマットが異なるだけです
t2 = tMcTestIS(Yvec)
println(sum(abs.(t.p - t2.p)) ≈ 0. ? "OK" : "error")

# 方法 (3) でも、入力データのフォーマットが異なるだけです
t3 = tMcTestIS([Yvec[m][1] for m=1:M], [Yvec[m][2] for m=1:M])
println(sum(abs.(t.p - t3.p)) ≈ 0. ? "OK" : "error")
```

**類似のテスト**

[`studentTest1S`](@ref) を参照してください ```
