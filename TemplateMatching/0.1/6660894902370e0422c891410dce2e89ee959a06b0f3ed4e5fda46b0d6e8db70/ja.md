ソースとテンプレートの間の二乗差を計算するアルゴリズム。

このメソッドは、ソース配列の各部分がテンプレートとどれだけ異なるかを、対応する値の差を二乗することで見つけるために使用されます。これは簡単で、画像の明るさがあまり変わらない場合にうまく機能します。値が低いほど、より良い一致を示します。

# 公式

$$
R_i = \sum_j (S_{i+j} - T_j)^2
$$

詳細は[`NormalizedSquareDiff`](@ref)を参照してください。
