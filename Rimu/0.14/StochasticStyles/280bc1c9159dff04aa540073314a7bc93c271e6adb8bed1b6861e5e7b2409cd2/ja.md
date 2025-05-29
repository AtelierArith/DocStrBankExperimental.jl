```
IsDynamicSemistochastic{T=Float64}(; kwargs...) <: StochasticStyle{T}
```

浮動小数点ウォーカ数とノイズを減らしたQMC伝播。構成内のウォーカ数が多い場合、すべての可能なスポーン（ベクトル-行列乗算におけるオフダイアゴナル要素）は決定論的に実行されます。これは`rel_spawning_threshold`および`abs_spawning_threshold`キーワードによって制御されます。スポーンの確率的選択は`spawning`キーワードによって制御されます。

デフォルトでは、消滅が完了した後に確率的ベクトル圧縮が適用されます。この動作は、`late_compression=false`を設定することでオンザフライの射影（[`IsStochasticInteger`](@ref)や[`IsStochasticWithThreshold`](@ref)のように）に変更できます。また、`spawning`と`compression`を変更することもできます。詳細な説明については以下のパラメータを参照してください。

## パラメータ:

  * `threshold = 1.0`: この数値未満の値は、この値またはゼロに確率的に射影されます。詳細は[`ThresholdCompression`](@ref)を参照してください。
  * `late_compression = true`: これが`true`に設定されている場合、すべてのスポーンが実行された後に確率的ベクトル圧縮が行われます。`false`に設定されている場合、値はスポーンされる際に確率的に射影されます。`late_compression=true`は、`compression=`[`ThresholdCompression`](@ref)`(threshold)`および`spawning=`[`WithReplacement`](@ref)`()`を設定することと同等です。`late_compression=false`は、`compression=`[`NoCompression`](@ref)`()`および`spawning=WithReplacement(threshold)`と同等です。
  * `rel_spawning_threshold = 1.0`: 構成内のウォーカ数にこの閾値を掛けた値がオフダイアゴナルの数を超える場合、スポーンは決定論的に行われます。最良のパフォーマンスのためには1以上に設定する必要があります。
  * `abs_spawning_threshold = Inf`: 構成内のウォーカ数がこの値を超える場合、スポーンは決定論的に行われます。例えば、`abs_spawning_threshold = 0.1 * target_walkers`のように設定できます。
  * `spawning = WithReplacement()`: 非正確なスポーンに使用する[`SpawningStrategy`](@ref)。
  * `compression = ThresholdCompression(threshold)`: ステップ後にベクトルを圧縮するために使用される[`CompressionStrategy`](@ref)。`threshold`を上書きします。

詳細は[`StochasticStyle`](@ref)を参照してください。
