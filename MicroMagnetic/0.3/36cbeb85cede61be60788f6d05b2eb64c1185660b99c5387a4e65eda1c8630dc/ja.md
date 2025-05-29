```
relax(sim::AbstractSim; max_steps=10000, stopping_dmdt=0.01, save_data_every=100, 
       save_m_every=-1, using_time_factor=true)
```

システムを `LLG` または `SD` ドライバーを使用してリラックスさせます。この関数は、[マイクロ磁気モデル](@ref) と [原子スピンモデル](@ref) の両方と互換性があります。

**引数:**

  * `max_steps::Int`: シミュレーションを実行する最大ステップ数。デフォルトは `10000` です。
  * `stopping_dmdt::Float64`: `LLG` および `SD` ドライバーの両方に対する主な停止条件。標準的なマイクロ磁気シミュレーションでは、典型的な値は `0.01` から `1` の範囲です。時間が厳密に定義されていない `SD` ドライバー モードでは、`γ` の因子が適用され、`LLG` ドライバーと比較できるようになります。次元のない単位を使用する原子モデルの場合、`using_time_factor` を `false` に設定してこの因子を無効にします。
  * `save_data_every::Int`: エネルギーや平均磁化などの全体データを保存する間隔。負の値はデータ保存を無効にします（例: `save_data_every=-1` はリラクゼーションの最後にのみデータを保存します）。
  * `save_m_every::Int`: 磁化データを保存する間隔。負の値は磁化保存を無効にします。
  * `using_time_factor::Bool`: `SD` モードで `LLG` モードと比較するために時間因子を適用するブールフラグ。デフォルトは `true` です。

**例:**

```julia
    relax(sim, max_steps=10000, stopping_dmdt=0.1)
```
