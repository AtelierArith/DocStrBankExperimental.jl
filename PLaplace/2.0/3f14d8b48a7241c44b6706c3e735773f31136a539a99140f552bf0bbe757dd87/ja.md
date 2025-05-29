```julia
mutable struct PLaplaceData
```

p-Laplace問題の解のための主な出力タイプ。pLaplace問題の解によって得られたすべてのパラメータと結果を格納します。[Statistics](@ref)、[Error Analysis](@ref)および解を.vtkファイルに書き込むために使用できます。

# フィールド

  * `mesh::MinFEM.Mesh`: 計算領域のメッシュ。
  * `dirichlet_nodes::Set{Int64}`: 計算領域のディリクレ境界。
  * `fixed_nodes::Union{Missing, Set{Int64}}`: 計算領域の境界上の固定ノード。
  * `neumann_elements::Union{Missing, Set{Int64}}`: 計算領域のノイマン境界。
  * `f::Union{Missing, AbstractVector{Float64}}`: 領域のソース項。
  * `h::Union{Missing, AbstractVector{Float64}}`: ノイマン境界条件。
  * `qdim::Int64`: 解の成分数。
  * `p::Float64`: PDEパラメータ。
  * `gradient_bound::Union{Missing, Float64}`: 解の勾配の上限。
  * `eps::Float64`: 変分的意味での解の精度。
  * `stepsize::PLaplace.Stepsize`: 内点法のステッピングスキーム。
  * `Naux::Union{Missing, Int64}`: 補助的なパスフォローの反復回数。アルゴリズムが補助段階に達しなかった場合は欠損します。
  * `Nmain::Union{Missing, Int64}`: 主なパスフォローの反復回数。アルゴリズムが主段階に達しなかった場合は欠損します。
  * `tsetup::Union{Missing, Float64}`: セットアップに必要な時間。アルゴリズムがセットアップ段階に達しなかった場合は欠損します。
  * `taux::Union{Missing, Float64}`: 補助的なパスフォローに必要な時間。アルゴリズムが補助段階に達しなかった場合は欠損します。
  * `tmain::Union{Missing, Float64}`: 主なパスフォローに必要な時間。アルゴリズムが主段階に達しなかった場合は欠損します。
  * `calculation_nodes::Union{Missing, Set{Int64}}`: 解が計算されたノード、すなわちディリクレ条件のないノード。アルゴリズムがセットアップ段階で失敗した場合は欠損します。
  * `g::Union{Missing, AbstractVector{Float64}}`: 全領域に延長されたディリクレ境界条件。アルゴリズムがセットアップ段階で失敗した場合は欠損します。
  * `u::Union{Missing, AbstractVector{Float64}}`: 延長された境界条件のない計算ノード上のシフトされた解。アルゴリズムが収束しなかった場合は欠損します。
  * `v::Union{Missing, AbstractVector{Float64}}`: p-Laplace問題の解。アルゴリズムが収束しなかった場合は欠損します。
  * `msg::String`: 反復からの通知。特にソルバーや前処理器の変更、早期停止に関する情報を含みます。
