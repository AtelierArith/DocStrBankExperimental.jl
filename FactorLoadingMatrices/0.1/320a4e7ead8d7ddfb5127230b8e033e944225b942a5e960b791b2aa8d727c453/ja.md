`nfactor` 潜在変数を `nx` 観測変数にマッピングするための負荷の行列を構築します。上三角はすべてゼロで、負荷ベクトル間の線形独立性を強制します。

# 引数

  * `values::AbstractVector`: 非ゼロの下三角に配置する値のベクトル。これらは左から右に列を下に走る順序で埋め込まれます。
  * `nx::Integer`: データの次元、すなわち負荷行列の行数
  * `nfactor::Integer`: 因子の数、すなわち負荷行列の列数
