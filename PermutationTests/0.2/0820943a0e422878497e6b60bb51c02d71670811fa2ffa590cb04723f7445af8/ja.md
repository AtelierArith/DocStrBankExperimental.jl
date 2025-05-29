```julia
# METHOD (2)
function anovaMcTestRM(Yvec::UniDataVec²; <same kwargs>)
```

**METHOD (1)**

データの置換による複数比較 [1-way 分散分析 (ANOVA) for repeated measures](https://en.wikipedia.org/wiki/Repeated_measures_design#Repeated_measures_ANOVA)。$M$ 個の仮説があり、それぞれに $K$ 回の繰り返し測定（例：処置、時間など）が $N$ 個の観察単位（例：被験者、ブロックなど）ごとにあるとします。帰無仮説は次の形を持ちます。

$$
H_0(m): μ_{m1}= \ldots =μ_{mk}, \quad m=1...M
$$

、

ここで $μ_{mk}$ は $m^{th}$ 仮説の $k^{th}$ 処置の平均です。

`Y` は $M$ 個のベクトルを保持するベクトルであり、それぞれが $K$ 個の処置（処置 1,..., 処置 $K$）を $m^{th}$ 仮説の各観察のためにこの順序で連結しています：観察 1 の $K$ 個の処置、観察 2 の $K$ 個の処置、...、観察 $N$ の $K$ 個の処置。したがって、`Y` は $N \cdot K$ 要素の $M$ 個のベクトルを保持します。

`ns` は形式 `(n=N, k=K)` のジュリア [名前付きタプル](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types) です（以下の例を参照）。

オプションのキーワード引数 `direction`、`switch2rand`、`nperm`、`seed`、`verbose`、`stepdown`、`fwe` および `threaded` の詳細は [こちら](@ref "Common kwargs for multiple comparisons tests") を参照してください。

*方向性テスト、置換スキームおよび正確なテストのための置換回数:* *単変量バージョン* [`anovaTestRM`](@ref) に従います。

*エイリアス:* `fTestMcRM`

[MultcompTest](@ref) 構造体を返します。

**METHOD (2)**

（1）と同様ですが、`Yvec` は $M$ 個のベクトルのベクトルであり、それぞれが $N$ 個のベクトルを保持し、各ベクトルが $n^{th}$ 被験者の $K$ 個の処置を保持しています（以下の例を参照）。

*Examples*

```julia
# method (1)
using PermutationTests
N=6 # 処置ごとの観察単位の数
K=3 # 処置の数
M=10 # 仮説の数
Yvec = [[randn(K) for n=1:N] for m=1:M]; # 例としてのランダムなガウスデータ
t = fMcTestRM([vcat(yvec...) for yvec in Yvec], (n=N, k=K)) 
# ANOVA テストは常に双方向です
```

```julia
# 5000 回のランダムな置換で近似テストを強制
tapprox = fMcTestRM([vcat(yvec...) for yvec in Yvec], (n=N, k=K); 
            switch2rand=1, nperm=5000)

# method (2) では入力データのフォーマットが異なるだけです
 
t2 = fMcTestRM(Yvec)
println(sum(abs.(t.p - t2.p)) ≈ 0. ? "OK" : "error")
println(sum(abs.(t.obsstat - t2.obsstat)) ≈ 0. ? "OK" : "error")
```

**Similar tests**

[`anovaTestRM`](@ref) を参照してください。
