```
pairwise_Gowdis(trait_matrix::Trait_Matrix, weight, species1::String, species2::String)
```

トレイトマトリックス内の種のペア間のGower距離を計算します。

# 引数

  * `trait_matrix::Trait_Matrix`: 種のトレイトデータを含むトレイトマトリックス。
  * `weight`: トレイトマトリックス内の各トレイトに対する重みパラメータのベクトル。欠損する場合があり、その場合は各トレイトは等しいと見なされます。
  * `species1::String`: 最初の種の名前。
  * `species2::String`: 2番目の種の名前。

# 戻り値

  * 2つの種間のGower距離。

# 詳細

この関数は、与えられたトレイトマトリックス内のトレイトデータに基づいて、種のペア間のGower距離を計算します。Gower距離は、異なるタイプの変数（カテゴリカル、数値、順序）とそれぞれの重みを考慮した非類似性の尺度です。非類似性は各トレイト変数について計算され、その後、提供された重みを使用して最終的なGower距離を取得します。

[`matrix_Gowdis`](@ref)も参照してください。
