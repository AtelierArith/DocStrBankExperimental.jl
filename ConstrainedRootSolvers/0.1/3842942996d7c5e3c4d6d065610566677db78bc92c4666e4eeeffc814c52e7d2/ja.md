このメソッドは[`Bisection`](@ref)メソッドを使用して最大値を見つけます。このメソッドが行うことは

  * まず`x_min`、`x_mid`、および`x_max`で`y`を計算する
  * `y`が最大になる点を見つける
  * その点から`x_min`と`x_max`に対して二分法を行う
  * `x_min`、`x_mid`、および`x_max`を更新する

    find_peak(f::Function,             ms::BisectionMethod{FT},             tol::Union{ResidualTolerance{FT}, SolutionTolerance{FT}};             stepping::Bool = false   ) where {FT<:AbstractFloat}

解を見つけるために、次のものが必要です。

  * `f` 解くべき関数
  * `ms` [`BisectionMethod`](@ref)型メソッド構造体
  * `tol` [`SolutionTolerance`](@ref)型許容誤差構造体
  * `stepping` オプション。trueの場合、最適化ステップをメソッド構造体の履歴フィールドに保存します。
