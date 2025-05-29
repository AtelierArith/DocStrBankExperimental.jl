```
tempered(sampler, inverse_temperatures; kwargs...)
OR
tempered(sampler, num_temps; swap_strategy=ReversibleSwap(), kwargs...)
```

提供された `inverse_temperatures` または `num_temps` から生成された逆温度と `swap_strategy` を使用して、`sampler` の温度付きバージョンを返します。

# 引数

  * `sampler` は、基礎的なサンプリングに使用され、温度付けを適用するためのアルゴリズムまたはサンプラーオブジェクトです。
  * 温度スケジュールは、明示的に定義するか、整数の温度数として定義できます。すなわち、次のように：

      * 逆温度のシーケンス {β₀, ..., βₙ} を含む `inverse_temperatures` で、0 ≤ βₙ < ... < β₁ < β₀ = 1     または
      * 生成された `inverse_temperatures` に含める逆温度の整数の数を指定する `num_temps`

# キーワード引数

  * `swap_strategy::AbstractSwapStrategy` は、チェーン間で逆温度を交換する方法を指定します。
  * `steps_per_swap::Integer` は、交換の試行の間に実行されるステップ数です。

# 参照

  * [`TemperedSampler`](@ref)
  * 交換戦略についての詳細：

      * [`AbstractSwapStrategy`](@ref)
      * [`ReversibleSwap`](@ref)
      * [`NonReversibleSwap`](@ref)
      * [`SingleSwap`](@ref)
      * [`SingleRandomSwap`](@ref)
      * [`RandomSwap`](@ref)
      * [`NoSwap`](@ref)

```
