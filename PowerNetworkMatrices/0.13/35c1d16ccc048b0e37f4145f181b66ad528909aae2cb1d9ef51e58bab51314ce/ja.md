```julia
LODF(A, ABA, BA; linear_solver, tol, reduce_radial_branches)

```

インシデンス行列とシステムのPTDF行列を用いてLODF行列を構築します。

注意: このメソッドは分散スラックバスをサポートしていません。

# 引数

  * `A::IncidenceMatrix`:       システムのインシデンス行列を含む構造体。
  * `ABA::ABA_Matrix`:       システムのABA行列を含む構造体。
  * `BA::BA_Matrix`:       システムの転置BA行列を含む構造体。
  * `linear_solver::String`:       使用する線形ソルバー。オプションは「Dense」と「KLU」です。
  * `tol::Float64`:       LODF行列のエントリを排除するための許容誤差（デフォルトはeps()）。
  * `reduce_radial_branches::Bool`:       放射状ブランチを簡素化し、排除するバスをマッピングすることでネットワークを縮小する場合はTrue。
