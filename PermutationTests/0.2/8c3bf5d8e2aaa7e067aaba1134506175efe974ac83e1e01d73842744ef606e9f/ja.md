```julia
function chiSquaredTest(table::Matrix{I};
            direction::TestDir = Both(),
            equivalent::Bool = true,
            switch2rand::Int = Int(1e8),
            nperm::Int = 20_000, 
            seed::Int = 1234, 
            verbose::Bool = true,
            asPearson::Bool = true) where {I <: Int, TestDir <: TestDirection}

```

単変量 [カイ二乗](https://en.wikipedia.org/wiki/Chi-squared_test) ($\chi^2$) の置換検定は、$2 \cdot K$ のコンティンジェンシーテーブルに対して行われ、ここで $K$ は ≥2 です。帰無仮説は次の形を持ちます。

$$
H_0: O=E
$$

,

ここで $O$ と $E$ はコンティンジェンシーテーブルの観測頻度と期待頻度です。

`table` は整数の行列の形で与えられるコンティンジェンシーテーブルです。例えば、次のコンティンジェンシーテーブルは

| 0 | 2 | 3 | 失敗 

| 3 | 1 | 0 | 成功

として与えられます。

```julia
table=[0 2 3; 3 1 0]
```

オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests")を参照してください。

$$
K=2
$$

の場合、この関数は [`studentTestIS`](@ref) を呼び出し、引数 `asPearson` も渡します。それ以外の場合は [`anovaTestIS`](@ref) を呼び出し、引数 `asPearson` は無視されます。

ピアソンの漸近的 $\chi^2$ と対照的に、置換検定ではサンプルサイズは大きくある必要はありません。実際、大きなサンプルサイズの場合、ピアソンの検定の方が効率的です。小さなサンプルサイズの場合、p値はすべての可能な置換を使用して得ることができ、したがって正確であり、[フィッシャーの正確検定](https://en.wikipedia.org/wiki/Fisher%27s_exact_test)を使用して得られるp値と同じになります。

したがって、この置換検定は標準の $\chi^2$ およびフィッシャーの正確検定と比較して特に有用ではありませんが、その多重比較バージョンはデータの置換を通じて家族全体の誤り率を制御することを可能にします。

*方向性検定*

$$
𝐾=2
$$

の場合のみ可能であり、この場合、検定はフィッシャーの正確検定に簡略化され、検定の方向性はキーワード引数 `direction` によって与えられます。関数 [`fisherExactTest`](@ref) とその多重比較バージョン [`fisherExactMcTest`](@ref) を参照してください。

*置換スキーム:* コンティンジェンシーテーブルは、各列の合計に応じた観測値を保持する $K$ のベクトルに変換されます。この変換は内部的に関数 [`table2vec`](@ref) によって行われます。ベクトルの要素は、対応する列の2つのセルのカウントと同じ数のゼロと1です。独立サンプルの1-way ANOVAのF統計量は、$\chi^2$ の同等の検定統計量となり、そのANOVAの置換スキームが適用されます（[`anovaTestIS`](@ref) を参照）。

*正確な検定のための置換の数:* 可能な置換の数は $\frac{N!}{N_1 \cdot\ldots\cdot N_K}$ であり、ここで $K$ はコンティンジェンシーテーブルの列の数、$N_k$ は $k^{th}$ 列の合計です。

*エイリアス:* `Χ²Test`、[`fisherExactTest`](@ref)

*多重比較バージョン:* [chiSquaredMcTest](@ref)

[UniTest](@ref) 構造を返します。

*例*

```julia
using PermutationTests
table=[0 2 2; 3 1 0]
t=Χ²Test(table) # 検定は双方向です
```

```julia
table=[6 1; 2 5]
tR=fisherExactTest(table; direction=Right()) 
# または tR=Χ²Test(table; direction=Right())
```
