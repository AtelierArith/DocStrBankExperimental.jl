```julia
# 方法 (2)
function anovaTestRM(yvec::UniDataVec; <同じキーワード引数>)
```

方法 (1)

データの置換による単変量 [1-way 分散分析 (ANOVA)](https://en.wikipedia.org/wiki/Repeated_measures_design#Repeated_measures_ANOVA) の反復測定。各 $N$ 観測単位（例：被験者、ブロックなど）に対して $K$ 回の反復測定（例：処置、時間など）が与えられた場合、帰無仮説は次の形を持ちます。

$$
H_0: μ_1= \ldots =μ_K
$$

,

ここで $μ_k$ は $k^{th}$ 処置の平均です。

`y` は、各観測に対してこの順序で $K$ 処置（処置 1,..., 処置 $K$）を連結したベクトルです：観測 1 の $K$ 処置、観測 2 の $K$ 処置、...、観測 $N$ の $K$ 処置。したがって、`y` には $N \cdot K$ 要素が含まれます。

`ns` は、形式が `(n=N, k=K)` のジュリア [名前付きタプル](https://docs.julialang.org/en/v1/manual/types/#Named-Tuple-Types) です（以下の例を参照）。

オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests") を参照してください。

*方向性テスト*

$$
𝐾=2
$$

の場合のみ可能で、この場合テストは2つの処置の差に対する1サンプルのスチューデントのt検定に簡略化され、テストの方向性はキーワード引数 `direction` によって与えられます。関数 [`studentTest1S`](@ref) とその多重比較バージョン [`studentMcTest1S`](@ref) を参照してください。

*置換スキーム:* 帰無仮説の下では、$K$ 測定の順序には意味がありません。交換可能性スキームは、$N$ 観測単位内で $K$ 測定を再配置することから成ります。

*正確なテストのための置換の数:* $N$ のすべての観測単位における $K$ 測定の再配置の方法は $K!^N$ 通りあります。

**エイリアス:** `fTestRM`

*多重比較バージョン:* [anovaMcTestRM](@ref)

両方の方法は [UniTest](@ref) 構造体を返します。

方法 (2)

(1) と同様ですが、`yvec` は $N$ のベクトルで、各ベクトルは $n^{th}$ 被験者の $K$ 処置を保持します（以下の例を参照）。

*例*

```julia
# (1)
using PermutationTests
N=6; # 観測単位の数
K=3; # 測定の数
y = [randn(K) for n=1:N] # 例としてのいくつかのランダムなガウスデータ
t = fTestRM(vcat(y...), (n=N, k=K)) # ANOVA テストは常に双方向です
```

```julia
# 5000 回のランダムな置換で近似テストを強制
tapprox = fTestRM(vcat(y...), (n=N, k=K); switch2rand=1, nperm=5000)
```

```julia
# 方法 (2) では、入力データのフォーマットの仕方だけが異なります
t2 = fTestRM(y)
println(t.p ≈ t2.p ? "OK" : "error")
```

**類似のテスト**

通常、入力データは実数ですが、整数またはブール型でも可能です。二項データの場合、この関数を使用すると、$K>2$ の場合の置換ベースのコクランQテストと $K=2$ の場合の置換ベースのマクネマー検定を取得できますが、正確なp値を提供する能力があります。これらの2つのテストには、専用の関数 [`cochranqTest`](@ref) と [`mcNemarTest`](@ref) が用意されています。
