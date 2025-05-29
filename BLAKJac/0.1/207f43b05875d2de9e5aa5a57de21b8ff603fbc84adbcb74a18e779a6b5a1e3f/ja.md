BLAKJac*analysis!(sequence::BlochSimulator, trajectorySet::Vector{<:Vector{<:TrajectoryElement}}, options::Dict, saved*H::Dict=Dict())

BLAKJac_Analysis! は、RF パターンと位相エンコーディングパターンを考慮してノイズレベルを予測します。

# 入力:

RF パターン、位相エンコーディングパターン、および一連のパラメータを含むシーケンスオブジェクト（以下を参照）

# 出力:

  * noisesAll   3 つのノイズ値 (rho, T1, T2) の配列
  * ItotAll     情報量 (まだ非常に生の指標)
  * b1factorsRMS (rho, T1, T2) と B1 の間の結合の配列 (および T1T2set にわたる RMS); handleB1=="sensitivity" の場合のみ計算されます
  * CSF_penalty  CSF 感度のペナルティ; CSF を考慮する場合のみ計算されます

# 入出力:

H 行列配列の辞書 (T1T2 プロービングインデックスと RF パターン名の組み合わせでラベル付け)

# パラメータ:

（注: 意味のあるオプションのセットは "options = Dict(); BLAKJac.BLAKJac_defaults!(trajectorySet, options)" によって事前に定義できます）

  * `account_SAR`   true の場合、SAR が最適化に考慮されます
  * `considerCyclic`   true に設定されている場合、シーケンスの開始時の磁化状態が終了時と同じであると仮定されます。
  * `emphasize_low_freq`   true の場合、(ky,kz) の最も中心的な領域により高い重みが与えられます
  * `handleB1`   デフォルトでは ("no")、再構成されるパラメータは T1, T2 および rho のみであると仮定されます; handleB1=="co-reconstruct" の場合、BLAKJac はこれも再構成可能なパラメータであると仮定します。handleB1=="sensitivity" の場合、b1factorRMS を計算します
  * `invregval`   再構成において仮定される正則化行列の対角成分の (逆数の) 配列: 0 の値は正則化が課されないことを仮定し、1 の値は再構成が T1 および T2 の参照値と等しくなることを非常に強く課すことを仮定します。invregval が `abs_sensitivity^2` のオーダーであるときにブレークイーブンが発生します。ここで `abs_sensitivity` は T1, T2 およびシーケンスに応じておおよそ 0.05 のオーダーです (非常に大まかに、T2/T1)。期待される SNR が 1 よりもはるかに大きい場合 (例: 10)、invregval はかなり小さくする必要があります。例: 0.005^2。
  * `lambda_B1`  B1 感度のための正則化パラメータ
  * `lambda_CSF` CSF 感度のための正則化パラメータ
  * `maxMeas`   デフォルト (BLAKJac_defaults) では、特定の (ky,kz) 組み合わせが測定中に見られる最大回数の 4 倍に設定されます。
  * `maxstate`   EPG 推定の信号と導関数が考慮する最大状態数
  * `nky`   デフォルト (BLAKJac_defaults) では、適用される ky 値の範囲
  * `nkz`   デフォルト (BLAKJac_defaults) では、適用される kz 値の範囲
  * `plotfuncs`   (BLAKJac_defaults!() によって埋められます; 適応しないでください)
  * `plottypes`   文字列の配列。配列に認識された文字列が含まれている場合、プロットが生成されます

| 文字列                 | 説明                                            |
|:------------------- |:--------------------------------------------- |
| "first"             | 各軌道の最初のサンプルの ky と kz に沿って RF 形状をプロットします       |
| "trajectories"      | 最初の 10 軌道をプロットします                             |
| "noisebars"         | ノイズレベルの棒グラフ                                   |
| "weights"           | 時間にわたる T1 および T2 感度のカラフルなプロット                 |
| "original_jacobian" | (説明予定)                                        |
| "noiseSpectrum"     | ky にわたるノイズスペクトル密度のグラフ、T1 マップ用と T2 マップ用の 1 つずつ |
| "infocon"           | (説明予定)                                        |

  * `rfFile`   H 行列辞書にタグ付けするために使用されるテキスト
  * `sigma_ref`   (情報量の計算に使用)
  * `startstate`   1 (反転前パルスなしを意味する) または -1 (実際のシーケンスの 1 TR 前に反転前パルスを意味する)
  * `T1ref`   "参照" T1 値
  * `T2ref`   "参照" T2 値
  * `T1T2set`   BLAKJac が評価される (T1,T2) 値のセット。通常は "7 ポイントミックス" (ToDo: これを再設計する)
  * `TR`  秒単位
  * `useSurrogate`  デフォルトでは false であるべき; true の場合、実際の EPG 推定ではなく、信号と導関数の多項式推定を使用します
  * `useSymmetry`   true の場合、プロトン密度の位相が非常に滑らかであると仮定され、BLAKJac 分析のすべての出力は実数であると見なされます
