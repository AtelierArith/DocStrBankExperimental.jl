`rms_clean_rvs_vs_num_basis_scalpels(rvs, ccfs; σ_rvs, max_num_basis )` 生のRVSをCCFsに基づいてScalpelsアルゴリズムでクリーンアップした後の推定RVのRMSを計算します。

入力:

  * rvs: 推定された放射速度のベクトル
  * ccfs: サイズ(num*velocities, num*spectra)のCCFSの2次元配列

オプションの入力:

  * σ_rvs: 推定された放射速度の測定不確実性のベクトル（デフォルト: ones）
  * max*num*basis: CCFのSVD再構成に使用する最大基底ベクトル数
  * sort*by*responce: RV応答によって基底ベクトルをソートするためにtrueを設定（デフォルト: true）

出力: rms_scalpels: 基底ベクトルの数の関数として、スカルペルによってクリーンアップされた後の推定RVのRMSのベクトル

注意:

  * 現在、Scalpelsはすべての観測を同等に重み付けし、σ_rvsを使用していません。
  * 出力の最初の要素は、ゼロ基底ベクトル（すなわち、入力RVs）でのRMSから始まります。
