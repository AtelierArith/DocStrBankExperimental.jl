```julia
function cochranqTest(table::Matrix{I};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true) where {I <: Int, TestDir <: TestDirection}

```

単変量 [Cochran Q](https://en.wikipedia.org/wiki/Cochran's_Q_test) テストはデータの置換によって行われます。Cochran Q テストは、繰り返し測定の 1-way ANOVA に類似していますが、二項データ（ゼロと1）を入力として受け取ります。$N$ の観察単位（例：被験者、ブロックなど）と $K$ の繰り返し測定（例：処置、時間など）が与えられた場合、帰無仮説は次の形になります。

$$
H_0: μ_1= \ldots =μ_K
$$

,

ここで $μ_k$ は $k^{th}$ 測定の平均です。

$$
K=2
$$

の場合、テストは [McNemar テスト](https://en.wikipedia.org/wiki/McNemar's_test) に簡略化され、これは二項データ（ゼロと1）を入力として受け取る繰り返し測定のための Student の t テストに類似しています。

入力 `table` は $N \cdot K$ のゼロと1のテーブルであり、$N$ は観察の数、$K$ は繰り返し測定です。転置すると、次のようなデータになります。

| 1 | 1 | 1 | 1 | 1 | 1 | 測定 1

| 1 | 0 | 1 | 1 | 0 | 1 | 測定 2

| 0 | 0 | 1 | 0 | 1 | 0 | 測定 3

このテーブルは、`table=[1 1 0; 1 0 0; 1 1 1; 1 1 0; 1 0 1; 1 1 0]` のように入力として与えられ、内部的に関数 [`table2vec`](@ref) によって適切な形式に変換されます。

!!! note "冗長な置換"
    テーブルに任意の組み合わせでベクトル `[0 0 0]` または `[1 1 1]` を追加すると、系統的な置換を使用しても同じ p 値が得られますが、リストされる置換の数が増加します。データにそのようなベクトルが存在する場合は、削除してテストを高速化できます。


オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests")を参照してください。

[Cochran Q](https://en.wikipedia.org/wiki/Cochran's_Q_test) および [McNemar](https://en.wikipedia.org/wiki/McNemar's_test) の漸近的テストとは対照的に、置換テストではサンプルサイズは大きくある必要はありません。実際、大きなサンプルサイズの場合、Cochran Q および McNemar テストはより効率的ですが、正確な p 値を提供しません（$K=2$ の場合の正確なテストは導出可能です）。全体として、この置換テストは標準の Cochran Q および McNemar テストと比較してあまり有用ではありませんが、その多重比較バージョンはデータの置換によって家族単位の誤り率を制御することを可能にします。

*方向性テスト*

$$
𝐾=2
$$

の場合のみ可能で、この場合テストは MnNemar テストに簡略化され、テストの方向性はキーワード引数 `direction` によって与えられます。関数 [`mcNemarTest`](@ref) およびその多重比較バージョン [`mcNemarMcTest`](@ref) を参照してください。

*置換スキーム:* 繰り返し測定の 1-way ANOVA の F 統計量は、Cochran Q テストの同等のテスト統計量であり、その ANOVA の置換スキームが適用されます（[`anovaTestRM`](@ref) を参照）。$K=2$ の場合（McNemar テスト）の置換スキームは同じです。

*正確なテストのための置換の数:* $K!^N$ 通りの方法で、すべての $N$ 観察単位における $K$ 測定を再配置することが可能です。

*エイリアス:* `qTest`, `mcNemarTest`

*多重比較バージョン:* [`cochranqMcTest`](@ref), [`mcNemarMcTest`](@ref)

[UniTest](@ref) 構造を返します。

*例*

```julia
using PermutationTests
table=[1 1 0; 1 0 0; 1 1 1; 1 1 0; 1 0 1; 1 1 0]
t=qTest(table) # テストは双方向です
```
