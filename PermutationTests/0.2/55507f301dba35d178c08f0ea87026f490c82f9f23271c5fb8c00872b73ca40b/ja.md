```julia
function fisherExactTest(<same args and kwargs as `chiSquaredTest`>)
```

データの置換によって単変量[Fisherの正確な検定](https://en.wikipedia.org/wiki/Fisher's_exact_test)を実行します。[chiSquaredTest](@ref)のエイリアスです。$2 \cdot 2$のコンティンジェンシーテーブルに使用できます。この場合のコンティンジェンシーテーブルは次の形をしています：

| a | b |

| c | d |

  * 右方向の検定の場合、$a/c$は$b/d$を超えることが期待されます。逆の場合、検定は0.5より高いp値を返します。
  * 左方向の検定の場合、$b/d$は$a/c$を超えることが期待されます。逆の場合、検定は0.5より高いp値を返します。

!!! tip "Nota Bene"
    $$
    K=2
    $$

    の場合、任意の入力データ行列はその転置と同じp値を返します。


*多重比較バージョン:* [fisherExactMcTest](@ref)

[UniTest](@ref)構造体を返します。

*例*

```julia
using PermutationTests
table=[6 1; 2 5]
t=fisherExactTestTest(table) 
# または t=Χ²Test(table) # 双方向検定
```

```julia
tR=fisherExactTest(table; direction=Right())  # 右方向の検定
```
