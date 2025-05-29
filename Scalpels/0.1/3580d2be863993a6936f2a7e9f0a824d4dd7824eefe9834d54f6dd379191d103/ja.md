`clean_rvs_scalpels(rvs, ccfs; σ_rvs, num_basis )` 入力:

  * rvs:  推定された放射速度のベクトル
  * ccfs: サイズ(num*velocities, num*spectra)のCCFSの2d配列

オプションの入力:

  * σ_rvs: 推定された放射速度の測定不確実性のベクトル (デフォルト: ones)
  * num_basis: CCFのSVD再構成に使用する基底ベクトルの数
  * sort*by*responce: RV応答によって基底ベクトルをソートするためにtrueを設定 (デフォルト: true)

出力: rvs_clean: スカルペルによってクリーンアップされた推定RVsのベクトル

注意:

  * 現在、スカルペルはすべての観測を等しく重み付けし、σ_rvsを使用していません。
  * 出力の最初の要素は、ゼロ基底ベクトルでのRMSから始まります (すなわち、入力RVs)。
