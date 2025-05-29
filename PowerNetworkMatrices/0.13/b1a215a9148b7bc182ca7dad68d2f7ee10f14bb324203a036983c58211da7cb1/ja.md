```julia
LODF(A, PTDFm; linear_solver, tol, reduce_radial_branches)

```

システムのインシデンス行列とPTDF行列を考慮してLODF行列を構築します。

注意: tolはLODFのスパース化に関するものであり、PTDFのものではありません。PTDF行列は非スパース化されたものとして考慮する必要があります（PTDFメソッドを呼び出す際に"tol"引数は指定されていません）。

# 引数

  * `A::IncidenceMatrix`:       システムのインシデンス行列を含む構造体。
  * `PTDFm::PTDF`:       システムの転置PTDF行列を含む構造体。
  * `linear_solver::String`:       使用する線形ソルバー。オプションは"Dense"と"KLU"です。
  * `tol::Float64`:       LODF行列のエントリを削除するための許容誤差（デフォルトはeps()）。
  * `reduce_radial_branches::Bool`:       放射状ブランチを簡素化し、削除するバスをマッピングすることでネットワークを削減する場合はTrue。
