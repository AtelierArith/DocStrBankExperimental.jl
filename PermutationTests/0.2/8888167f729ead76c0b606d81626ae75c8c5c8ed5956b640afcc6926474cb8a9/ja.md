```julia
# METHOD (3)
function studentTestIS(y1::UniData, y2::UniData; <same kwargs>)
```

**METHOD (1)**

単変量 [スチューデントのt検定（独立サンプル用）](https://en.wikipedia.org/wiki/Student's_t-test#Independent_(unpaired)_samples) データの置換による。2つのグループにおける $N=N1+N_2$ の観測値が与えられたとき、帰無仮説は次の形を持つ。

$$
H_0: μ_1=μ_2
$$

、

ここで $μ_1$ と $μ_2$ はそれぞれグループ1とグループ2の平均である。

双方向検定の場合、このt検定は2つの独立したサンプルに対する1-way ANOVAと同等である。しかし、ANOVAとは異なり、方向性を持つことができる。

`y` は2つのグループの観測値のベクトルを連結したベクトルである。したがって、$N$ 要素を保持する。

`ns` はグループの数を保持する整数のベクトルである（以下の例を参照）。

オプションのキーワード引数 `direction`、`equivalent`、`switch2rand`、`nperm`、`seed`、および `verbose` については、[こちら](@ref "Common kwargs for univariate tests")を参照。

`asPearson` がtrue（デフォルト）である場合、テストはピアソン相関検定の同等バージョンとして実行される。これは、t検定がより少ない置換を必要とするため、一般的には正確な単変量検定においては速くはないが、近似検定においては一般的に有利である（[ベンチマーク](@ref "Benchmarks")を参照）。正確な検定を実行する必要がある場合は、`asPearson` をfalseに設定することをお勧めする。

!!! note "注意"
    `asPearson` がtrueの場合、テスト結果の `.stat` フィールドは実際には `CrossProd()` となる。データはテストを実行する前に標準化されるためである。[`correlationTest`](@ref)を参照。


*方向性検定*

  * 右方向の検定の場合、$μ_1$ は $μ_2$ を超えることが期待される。逆の場合、テストはp値が0.5より高くなる。
  * 左方向の検定の場合、$μ_2$ は $μ_1$ を超えることが期待される。逆の場合、テストはp値が0.5より高くなる。

*置換スキーム:* 帰無仮説の下では、観測値のグループメンバーシップには意味がない。交換可能性スキームは、元のグループの数を尊重して2つのグループにおける$N$の観測値を再割り当てすることから成る。

*正確な検定のための置換の数:* 2つのグループにおける$N$の観測値の再割り当ては $\frac{N!}{N_1 \cdot N_2}$ 通り存在する。

*エイリアス:* `tTestIS`、[`pointBiSerialTest`](@ref)

*多重比較バージョン:* [`studentMcTestIS`](@ref)

[UniTest](@ref) 構造体を返す。

**METHOD (2)**

(1) と同様だが、`yvec` はグループ1とグループ2の観測値の2ベクトルのベクトルである（以下の例を参照）。

**METHOD (3)**

(1) と同様だが、観測値は2つのベクトル `y1` と `y2` として2つのグループに分けて与えられる（以下の例を参照）。

*例*

```julia
# (1)
using PermutationTests
ns=[4, 5]; # グループ1とグループ2の観測値の数 (N1 と N2)
y=[randn(n) for n∈ns]; # 例としてのいくつかのガウスデータ
t = tTestIS(vcat(y...), ns) # デフォルトではテストは双方向

# 双方向のテストでは、tは独立サンプルに対する1-way ANOVAと同等である
tanova= fTestIS(vcat(y...), ns) 
println(t.p ≈ tanova.p ? "OK" : "error")

# CrossProdテスト統計を使用して実行しない
tcor = tTestIS(vcat(y...), ns; asPearson=false) 

# 10000回のランダム置換で近似テストを強制する
tapprox = fTestIS(vcat(y...), ns; switch2rand=1, nperm=10000) 

tR=tTestIS(vcat(y...), ns; direction=Right()) # 右方向のテスト
tL=tTestIS(vcat(y...), ns; direction=Left()) # 左方向のテスト

# メソッド(2)では、入力データのフォーマットの仕方が異なるだけである
t2 = tTestIS(y)
println(t.p ≈ t2.p ? "OK" : "error")

# メソッド(3)でも、入力データのフォーマットの仕方が異なるだけである
t3 = tTestIS(y[1], y[2])
println(t.p ≈ t3.p ? "OK" : "error")

```

**類似のテスト**

通常、入力データは実数であるが、整数またはブール型でも可能である。

二項データの場合、この関数を使用すると、フィッシャーの正確検定によって与えられるのと同じp値を得ることができるが、この場合は、入力としてコンティンジェンシーテーブルを受け入れる[`fisherExactTest`](@ref)関数を使用する方が便利である。

この関数は、置換に基づくポイントバイセリアル相関検定を実行するためにも使用できる。専用の関数[`pointBiSerialTest`](@ref)を参照。
