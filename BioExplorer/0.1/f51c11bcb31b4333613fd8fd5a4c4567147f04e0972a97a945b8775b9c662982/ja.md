```
pielou_evenness(community_matrix::Community_Matrix)
```

Pielouのフレームワークに従った均等性多様性指標を計算します。

# 引数

  * `community_matrix::Community_Matrix`: 種の豊富さデータを含むコミュニティマトリックス。

# 戻り値

  * 各コミュニティのPielouの均等性（J）指標を含むDataFrame。

# 詳細

この関数は、与えられたコミュニティマトリックス内の各コミュニティに対してPielouの均等性（J）指標を計算します。Pielouの均等性は、コミュニティ内の種の豊富さ分布の均等性を測定します。これは、シャノン・ウィーナーエントロピーを最大可能エントロピー（種の多様性の対数）で割ったものとして計算されます。

# 参考文献

Pielou, E. C. (1969). An Introduction to Mathematical Ecology. Wiley-Interscience.
