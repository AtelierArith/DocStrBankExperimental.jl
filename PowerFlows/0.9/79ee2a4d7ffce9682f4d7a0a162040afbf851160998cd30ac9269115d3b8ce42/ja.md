すべての電力フローと角度の評価に必要なデータを含む構造体、およびこれらのデータ。

# 引数:

  * `bus_lookup::Dict{Int, Int}`:       システムのバス番号と「power*network*matrix」または「aux*network*matrix」の行をリンクする辞書。
  * `branch_lookup::Dict{String, Int}`:       ブランチ名と「power*network*matrix」または「aux*network*matrix」の列名をリンクする辞書。
  * `bus_activepower_injection::Matrix{Float64}`:       バスのアクティブ電力注入を含む "(b, t)" 行列。b: バスの数、t: 時間の期間。
  * `bus_reactivepower_injection::Matrix{Float64}`:       バスのリアクティブ電力注入を含む "(b, t)" 行列。b: バスの数、t: 時間の期間。
  * `bus_activepower_withdrawals::Matrix{Float64}`:       バスのリアクティブ電力引き出しを含む "(b, t)" 行列。b: バスの数、t: 時間の期間。
  * `bus_reactivepower_withdrawals::Matrix{Float64}`:       バスのリアクティブ電力引き出しを含む "(b, t)" 行列。b: バスの数、t: 時間の期間。
  * `bus_reactivepower_bounds::Matrix{Float64}`:       各バスの各時間期間におけるリアクティブ供給の上限と下限を含む "(b, t)" 行列。
  * `bus_type::Matrix{PSY.ACBusTypes}`:       システム内のバスのタイプを含む "(b, t)" 行列。「bus_lookup」に従って順序付けられた、各時間期間のバスのタイプ。
  * `bus_magnitude::Matrix{Float64}`:       バスの大きさを含む "(b, t)" 行列。「bus_lookup」に従って順序付けられた。b: バスの数、t: 時間の期間。
  * `bus_angles::Matrix{Float64}`:       バスの角度を含む "(b, t)" 行列。「bus_lookup」に従って順序付けられた。b: バスの数、t: 時間の期間。
  * `branch_activepower_flow_from_to::Matrix{Float64}`:       `from` バスで測定されたアクティブ電力フローを含む "(br, t)" 行列。「branch_lookup」に従って順序付けられた。br: ブランチの数、t: 時間の期間。
  * `branch_reactivepower_flow_from_to::Matrix{Float64}`:       `from` バスで測定されたリアクティブ電力フローを含む "(br, t)" 行列。「branch_lookup」に従って順序付けられた。br: ブランチの数、t: 時間の期間。
  * `branch_activepower_flow_to_from::Matrix{Float64}`:       `to` バスで測定されたアクティブ電力フローを含む "(br, t)" 行列。「branch_lookup」に従って順序付けられた。br: ブランチの数、t: 時間の期間。
  * `branch_reactivepower_flow_to_from::Matrix{Float64}`:       `to` バスで測定されたリアクティブ電力フローを含む "(br, t)" 行列。「branch_lookup」に従って順序付けられた。br: ブランチの数、t: 時間の期間。
  * `timestep_map::Dict{Int, S}`:       時間期間の番号（前述の行列の列番号に対応）とその名前をマッピングする辞書。
  * `valid_ix::Vector{Int}`:       スラックバスでないインデックスを含むベクター
  * `power_network_matrix::M`:       電力フローまたはバス角度の評価に使用される行列、考慮される方法に応じて。
  * `aux_network_matrix::N`:       電力フローまたはバス角度の評価に使用される行列、考慮される方法に応じて。
  * `neighbors::Vector{Set{Int}}`: 隣接バスのセットを持つベクター。
