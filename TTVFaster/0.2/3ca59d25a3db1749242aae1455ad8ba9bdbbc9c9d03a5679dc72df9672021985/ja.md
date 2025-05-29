ttv_wrapper(tt0)

平均線形エフェメリスとTTVFasterからのペアワイズTTVを追加して、トランジット時間を生成します。 現在、スキップされたトランジットは考慮されていません。 引数:   tt0:     惑星の初期トランジット時間   nplanet: モデル化する惑星の数   ntrans: 各惑星のモデルにおけるトランジットの数   params:  各惑星の5つの要素を保持します: mass_ratio, period, trans0, ecosw, esinw    jmax:    両惑星のTTV計算を合計する最大jを指定します。 戻り値:   tts:  観測された惑星のモデルトランジット時間とシステムのモデルTTV。
