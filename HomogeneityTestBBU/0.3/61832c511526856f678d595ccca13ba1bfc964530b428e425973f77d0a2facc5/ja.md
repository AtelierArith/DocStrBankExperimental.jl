```
homogeneity_test_fn
```

この関数は、Bugni、Bunting、Ura（2023）の均質性テストを実装しています。

## 引数

  * `X::Tuple`: タプルの形でデータを表す $X=(S, A)$、ここで A は空である可能性があります。
  * `test_stat_fn::Function`: 引数 $S$ と $A$（または $A=[~]$ の場合は $S$ のみ）を受け取り、テスト統計量の（ベクトル）を返す関数。
  * `K::Int`: MCMCチェーンの長さを示す整数。デフォルトは10,000です。
  * `verbose::Vector{String}`: ベクトルの可能な要素は `"P value"`、`"Test stat"`、および `"X^K"` です。デフォルトは空です。
  * `A_trivial::Boolean`: $S'=A$ であるかどうかを示すブール値。デフォルトは false です。

## 値

  * `Pvalue`: テストの p 値（Bugni、Bunting、Ura（2023）、式（4））。
  * `Pvalue_chain`: $K$ ステップごとに計算された p 値（オプション）。
  * `test_stat_chain`: $X$ に対して計算されたテスト統計量と $K$ ステップ（オプション）。
  * `X_K'`: 順列化されたデータを含むタプル（オプション）。
