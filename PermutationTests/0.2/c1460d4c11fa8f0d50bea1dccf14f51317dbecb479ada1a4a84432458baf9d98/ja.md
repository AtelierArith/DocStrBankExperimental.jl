```julia
# METHOD (2)
function anovaTestIS(yvec::UniDataVec; <same kwargs>)
```

**METHOD (1)**

独立サンプルのための[1-way 分散分析 (ANOVA)](https://en.wikipedia.org/wiki/One-way_analysis_of_variance)をデータの置換によって行います。$N=N1+...+N_K$の観測値が$K$グループにある場合、帰無仮説は次の形を持ちます。

$$
H_0: μ_1= \ldots =μ_K
$$

、

ここで$μ_k$は$k^{th}$グループの平均です。

`y`は各グループの観測値のベクトルを自然な順序で連結したベクトルです。したがって、$N$要素を保持します。

`ns`はグループの数を保持する整数のベクトルです（以下の例を参照）。

オプションのキーワード引数`direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および`verbose`については、[こちら](@ref "Common kwargs for univariate tests")を参照してください。

*方向性テスト*

$$
𝐾=2
$$

の場合にのみ可能で、この場合、テストは独立サンプルのためのStudentのt検定に簡略化され、テストの方向性はキーワード引数`direction`によって与えられます。関数[`studentTestIS`](@ref)およびその多重比較バージョン[`studentMcTestIS`](@ref)を参照してください。

*置換スキーム:* 帰無仮説の下では、観測値のグループメンバーシップには意味がありません。交換可能性スキームは、元のグループの数を尊重しながら$K$グループに$N$観測値を再割り当てすることから成ります。

*正確なテストのための置換の数:* $K$グループに$N$観測値を再割り当てる方法は$\frac{N!}{N_1 \cdot \ldots \cdot N_K}$通りあります。

**エイリアス:** `fTestIS`

*多重比較バージョン:* [anovaMcTestIS](@ref)

両方の方法は[UniTest](@ref)構造を返します。

**METHOD (2)**

(1)と同様ですが、`yvec`は各グループの観測値のK個のベクトルのベクトルです。

*例*

```julia
# (1)
using PermutationTests
ns=[4, 5, 6] # グループ1、2、3の観測数
yvec = [randn(n) for n in ns] # 例としてのいくつかのランダムなガウスデータ
t = fTestIS(vcat(yvec...), ns) # ANOVAテストは常に双方向です
```

```julia
# 5000回のランダム置換で近似テストを強制
tapprox = fTestIS(vcat(yvec...), ns; switch2rand=1, nperm=5000) 
```

```julia
# メソッド(2)では、入力データのフォーマットの仕方だけが異なります
t2 = fTestIS(yvec)
println(t.p ≈ t2.p ? "OK" : "error")
```

**類似のテスト**

通常、ANOVAの入力データは実数ですが、整数またはブール型でも可能です。二項データの場合、この関数を使用すると、$K \cdot 2$のコンティンジェンシーテーブルに対する置換ベースの[Χ²テスト](https://en.wikipedia.org/wiki/Chi-squared_test)を取得でき、正確なp値を提供する能力があります。$2 \cdot 2$のコンティンジェンシーテーブルの場合、[フィッシャーの正確検定](https://en.wikipedia.org/wiki/Fisher's_exact_test)とまったく同じp値を生成します。これらのケースでは、データ入力としてコンティンジェンシーテーブルを受け入れる[chiSquaredTest](@ref)および[fisherExactTest](@ref)関数を使用する方が便利です。
