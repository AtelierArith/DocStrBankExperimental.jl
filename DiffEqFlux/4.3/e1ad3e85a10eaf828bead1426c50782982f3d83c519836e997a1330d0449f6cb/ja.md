FFJORDは、`rand`を使用して新しいサンプルを生成したり、`pdf`または`logpdf`（`Distributions.jl`から）を使用して密度を推定するための分布として使用できます。

引数:

  * `model`: FFJORDインスタンス。
  * `regularize`: 正則化を使用するかどうか（デフォルト: `false`）。
  * `monte_carlo`: モンテカルロを使用するかどうか（デフォルト: `true`）。
