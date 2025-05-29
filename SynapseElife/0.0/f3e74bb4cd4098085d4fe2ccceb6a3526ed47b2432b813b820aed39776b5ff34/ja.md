```julia
dataProtocol(paper)

```

プラスチシティプロトコル「conoc」を説明する構造体

# 引数

  * `paper` は `["oconnor", "Bittner", "Goldings01", "Buchenan", "Tigaret_jitter_timespent", "Tigaret_jitter_double_1", "Poisson", "Tigaret_jitter", "Dudek_jitter", "TigaretMellor16", "TigaretMellor16_poisson", "Sleep_age", "Poisson_physiological_range", "YannisDebanne20_freq", "YannisDebanne20_freq_delay", "YannisDebanne20_ratio", "YannisDebanne20_inv", "Tigaret_burst", "Tigaret_burst_temp", "Tigaret_burst_age", "Tigaret_burst_freq", "Tigaret_burst_ca", "Tigaret_burst_dist", "Tigaret_freq_1200", "Tigaret_tripost", "Tigaret_preburst", "Tigaret_single", "TigaretMellor_sparse", "TigaretMellor_jitter_sparse", "DudekBear92-BCM-Ca", "DudekBear92-BCM", "DudekBear92-BCM-900", "DudekBear92-BCM-37", "DudekBear92-BCM-33", "DudekBear92-BCM-priming", "DudekBear92_timespend", "DudekBear92-100", "DudekBear_short", "FujiBito", "DudekBear92-sliding", "DudekBear92_temp", "DudekBear92_Ca", "DudekBear92_Mg", "DudekBear92_dist", "DudekBear92-Age", "Blocking_age_control", "Blocking_yNMDA", "Blocking_oNMDA", "Blocking_yBaP", "Blocking_oBaP", "Blocking_yGABA", "Blocking_oGABA", "DudekBear92_BCM_recovery", "DudekBear93-LFS", "DudekBear93-TBS", "Cao-TBS", "RecoverLTD", "Chang19", "Fujii_CaN", "YannisDebanne20", "YannisDebanne_temp", "YannisDebanne_age", "Meredith03-GABA", "TigaretvsMeredith", "YannisvsMeredith", "WittenbergWang06_D", "WittenbergWang06_B", "WittenbergWang06_P", "Mizuno01-LTP-Mg", "Mizuno01LTP", "Mizuno01LTD"]`
  * `n_pre` プレシナプスパルスの数
  * `delay_pre` プレシナプスパルス間の遅延
  * `n_pos` ポストシナプスパルスの数
  * `delay_pos` ポストシナプスパルス間の遅延
  * `delay` プレシナプスとポストシナプスのスパイク間の遅延（STDPで使用）
  * `pulse` パルス/ペアリングの繰り返し回数
  * `freq` 周波数
  * `causal` 因果関係がプレとポストの順序を反転させる、trueまたはfalseを使用
  * `protocol` プロトコルの名前
  * `weight` 重みの変化値を持つ情報エントリ（モデルでは使用されない）
  * `outcome` 定性的な結果を示す `String`（モデルでは使用されない）
  * `paper` paperは、事前定義されたプロトコルを選択するための `String`（例：paper = TigaretMellor16）
  * `temp` すべての温度感受性メカニズムが適応される温度
  * `injection` (nA) ソーマに注入される電流、ポストシナプススパイク（BaPs）を生成するために使用
  * `exca` (μM) 細胞外カルシウム、ghk関数で使用するためにμMで表現
  * `exmg` (mM) 細胞外マグネシウム、mMで表現されるが、マグネシウム緩和関数ではμMに変換される
  * `repeat_times` 追加のエポックを含めるためのエポックの数、例えばTBSは通常エポックで表現される
  * `repeat_after` エポック間の時間差（ms）
  * `testing_freq` 一部のプロトコルはテスト周波数を使用し、これにより効果の評価やそれがない場合の評価、または定期的な背景プレシナプス刺激を追加するのに役立つ。0 Hzはオフにする
  * `inj_time` BaPを引き起こすための電流注入の持続時間（ms）
  * `age` 動物の年齢（ラット）
  * `AP_by_EPSP` `yes` または `no`、EPSPによって誘発される追加のBaPSを刺激に含めるかどうか
  * `GABA_block` `yes` または `no` GABAr導電率をゼロに設定
  * `jitter` スパイクをジッターさせるために使用されるガウスの標準偏差
  * `sparse` スキップされたスパイクの割合
  * `dista` ソーマからの距離（μm）
