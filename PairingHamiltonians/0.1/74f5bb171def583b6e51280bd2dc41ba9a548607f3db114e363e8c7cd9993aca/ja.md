```
PairingHamiltonian(to; Norb_in::Int=8, Nocc_in::Int=4, gval::Float64=0.33, delta_eps::Float64=1.0,
                    debug_mode::Int=0, solver::String="FCI(2-fold)", save_Exact_wf::Bool=false)
```

ペアリングハミルトニアンの基底状態エネルギーを評価するためのメイン関数です。

# デフォルト値を持つオプション引数

  * `Norb_in::Int=8`: 軌道の数
  * `Nocc_in::Int=4`: 占有状態の数
  * `gval::Float64=0.33`: ペアリング強度
  * `delta_eps::Float64=1.0`: 軌道間のエネルギー差
  * `debug_mode::Int=0`: デバッグモードを指定
  * `solver::String("FCI(2-fold)")`: ハミルトニアンを解くための方法。この中から選択できます："Full-CI", "Full-CI(2-fold)", "HF", "BCS", "CCD", "IMSRG(2)"。 "HF"が選択された場合、PT2/PT3エネルギーも計算されます。
  * `save_Exact_wf::Bool(false)`: フルCI波動関数をHDF5ファイルとして保存します。これにより、波動関数の分析や固有ベクトル継続のような代理モデルの構築に使用できます。
  * `to`: 何も指定しないか、ユーザースクリプトで定義されたTimerOutputオブジェクト。
