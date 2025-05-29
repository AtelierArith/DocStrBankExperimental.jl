```julia
# METHOD (2)
function anovaMcTestIS(𝐘vec::UniDataVec²; <same kwargs>)
```

**METHOD (1)**

データの置換による複数比較 [1-way analysis of variance (ANOVA) for independent samples](https://en.wikipedia.org/wiki/One-way_analysis_of_variance)。

$$
M
$$

個の ANOVA を同時に実行します。入力データは、すべての観測値を連結した $M$ 個のベクトル $𝐲1,...,𝐲M$ を保持するベクトル `Y` として与えられます。これは、$K>2$ の独立したサンプル（グループ）に対して、各 $N=N_1+...+N_K$ の観測値を保持します。観測値は、グループ 1 が最初、その後グループ 2、...、最後にグループ K の順に並べられます。グループの数 $N_1,...,N_K$ は、すべての $M$ 仮説に対して同じでなければなりません。唯一のチェックは、`Y` の最初のベクトルに `sum(ns)` 要素が含まれていることです。

$$
M
$$

個の帰無仮説は次の形を持ちます。

$$
H_0(m): μ_{m1}= \ldots =μ_{mK}, \quad m=1...M
$$

、

ここで $μ_{mk}$ は $m^{th}$ 仮説に対する $k^{th}$ グループの平均です。

`ns` はグループの数 $N_1,...,N_K$ を保持する整数のベクトルです（以下の例を参照）。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` については、[こちら](@ref "Common kwargs for multiple comparisons tests")を参照してください。

方向性テスト、置換スキームおよび正確なテストのための置換の数：*単変量バージョン* [`anovaTestIS`](@ref) に従います。

*エイリアス:* `fMcTestIS`

[MultcompTest](@ref) 構造体を返します。

**METHOD (2)**

方法 (1) と同様ですが、入力データ `Yvec` はグループ 1、...、グループ K の観測値の $M$ 個のベクトルを保持するベクトルです。

*例*

```julia
# method (1)
using PermutationTests
ns=[3, 4, 5] # グループ 1、2、3 の観測数
M=10 # 仮説の数
Yvec = [[randn(n) for n in ns] for m=1:M]; # 例としてのランダムなガウスデータ
t = fMcTestIS([vcat(y...) for y in Yvec], ns) # ANOVA テストは常に双方向です

# 5000 回のランダムな置換で近似テストを強制
tapprox = fMcTestIS([vcat(y...) for y in Yvec], ns; switch2rand=1, nperm=5000) 

# 方法 (2) では、入力データのフォーマットが異なるだけです
t2 = fMcTestIS(Yvec)
# もちろん、方法 (1) と (2) は同じ p 値を与えます
println(sum(abs.(t.p-t2.p))≈0. ? "OK" : "error") 
```

**類似のテスト**

[`anovaTestIS`](@ref) を参照してください。
