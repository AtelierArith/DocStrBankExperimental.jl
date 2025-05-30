```
hill(community_matrix::Community_Matrix)
```

コミュニティマトリックス内のすべてのコミュニティに対してヒル系列を計算します。

# 引数

  * `community_matrix::Community_Matrix`: 複数のコミュニティの種の豊富さデータを含むコミュニティマトリックス。

# 戻り値

  * 各コミュニティのヒル系列を表すDataFrameで、ヒル数H0、H1、H2、およびH3が含まれます。

# 詳細

この関数は、与えられたコミュニティマトリックス内の各コミュニティに対して、異なるヒル数の順序での種の同等数を表すヒル系列を計算します。ヒル数は、種の豊富さを共通の単位にスケーリングすることによって生物多様性を測定し、異なるコミュニティ間での生物多様性を比較する方法を提供します。出力DataFrameには、各コミュニティのヒル数H0、H1、H2、およびH3が含まれています。

# 参考文献

Hill, M. O. (1973). Diversity and Evenness: A Unifying Notation and Its Consequences. Ecology, 54(2), 427–432. https://doi.org/10.2307/1934352
