```
sys = Scanner(B0, B1, Gmax, Smax, ADC_Δt, seq_Δt, GR_Δt, RF_Δt,
    RF_ring_down_T, RF_dead_time_T, ADC_dead_time_T)
```

Scanner構造体。MRI共鳴器のハードウェア制限を含んでいます。シミュレーションの入力です。

# 引数

  * `B0`: (`::Real`, `=1.5`, `[T]`) 主磁場強度
  * `B1`: (`::Real`, `=10e-6`, `[T]`) 最大RF振幅
  * `Gmax`: (`::Real`, `=60e-3`, `[T/m]`) 最大勾配振幅
  * `Smax`: (`::Real`, `=500`, `[mT/m/ms]`) 勾配の最大スルーレート
  * `ADC_Δt`: (`::Real`, `=2e-6`, `[s]`) ADCラスタ時間
  * `seq_Δt`: (`::Real`, `=1e-5`, `[s]`) シーケンスブロックラスタ時間
  * `GR_Δt`: (`::Real`, `=1e-5`, `[s]`) 勾配ラスタ時間
  * `RF_Δt`: (`::Real`, `=1e-6`, `[s]`) RFラスタ時間
  * `RF_ring_down_T`: (`::Real`, `=20e-6`, `[s]`) RFリングダウン時間
  * `RF_dead_time_T`: (`::Real`, `=100e-6`, `[s]`) RFデッドタイム
  * `ADC_dead_time_T`: (`::Real`, `=10e-6`, `[s]`) ADCデッドタイム

# 戻り値

  * `sys`: (`::Scanner`) Scanner構造体

# 例

```julia-repl
julia> sys = Scanner()

julia> sys.B0
```
