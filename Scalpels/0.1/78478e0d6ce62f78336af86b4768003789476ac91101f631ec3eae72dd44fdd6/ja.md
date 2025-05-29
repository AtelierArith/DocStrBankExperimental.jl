`calc_clean_rvs_scores_basis_scalpels(rvs, ccfs; σ_rvs, num_basis, sort_by_responce )` は、CCFのScalpels再構成のために、クリーンなrvsとCCF基底関数およびスコアを計算します。入力:

  * rvs: 推定された放射速度のベクトル
  * ccfs: サイズ(num*velocities, num*spectra)のCCFの2d配列

オプションの入力:

  * σ_rvs: 推定された放射速度の測定不確実性のベクトル（デフォルト: ones）
  * num_basis: CCFのSVD再構成に使用する基底ベクトルの数
  * sort*by*responce: RV応答によって基底ベクトルをソートするにはtrueを設定（デフォルト: true）

出力: (rvs, scores, basis): NamedTuple

ノート:

  * 現在、Scalpelsはすべての速度ピクセルを等しく重み付けし、各観測値にσ_rvsを使用します。
  * 出力の最初の要素は、ゼロ基底ベクトル（すなわち、入力RVs）で始まるRMSです。
