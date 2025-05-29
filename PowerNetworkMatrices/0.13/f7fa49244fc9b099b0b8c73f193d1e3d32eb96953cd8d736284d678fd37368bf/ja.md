```julia
PTDF(
    A,
    BA;
    dist_slack,
    linear_solver,
    tol,
    reduce_radial_branches
)

```

システムからPTDF行列を構築します。返されるのは、バス番号でインデックス付けされたPTDF配列です。

# 引数

  * `A::IncidenceMatrix`:       インシデンス行列（完全構造）
  * `BA::BA_Matrix`:       BA行列（完全構造）

# キーワード引数

  * `dist_slack::Vector{Float64}`:       分散スラックバスとして使用される重みのベクトル。       分散スラックベクトルは、バスの数と同じ長さでなければなりません。
  * `linear_solver::String`:       使用する線形ソルバー。オプションは「Dense」、「KLU」、「MKLPardiso」です。
  * `tol::Float64`:       PTDF行列のエントリを削除するための許容誤差（デフォルトはeps()）。
  * `reduce_radial_branches::Bool`:       ラジアルブランチを簡素化し、削除されたバスをマッピングすることによってネットワークを削減する場合はTrue。
