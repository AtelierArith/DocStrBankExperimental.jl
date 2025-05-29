```
StochasticStyle(v)
```

抽象型。関数として呼び出されると、シミュレーションの進行方法を決定する一般化ベクトル `v` のネイティブスタイルを返します。

# 使用法

具体的な `StochasticStyle` は、[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)、[`DVec`](@ref Main.DictVectors.DVec)、および [`PDVec`](@ref Main.DictVectors.PDVec) の `style` キーワード引数に使用できます。以下のスタイルが利用可能です：

  * [`IsStochasticInteger`](@ref Main.StochasticStyles.IsStochasticInteger)
  * [`IsDeterministic`](@ref Main.StochasticStyles.IsDeterministic)
  * [`IsStochasticWithThreshold`](@ref Main.StochasticStyles.IsStochasticWithThreshold)
  * [`IsDynamicSemistochastic`](@ref Main.StochasticStyles.IsDynamicSemistochastic)
  * [`StyleUnknown`](@ref Main.StochasticStyles.StyleUnknown)

# 拡張ヘルプ

## インターフェース

新しい `StochasticStyle` を定義する際は、`MyStyle<:StochasticStyle{T}` としてサブタイプ化します。ここで `T` はスタイルが対応する具体的な値の型です。

[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) で機能させるためには、`StochasticStyle` は以下を定義する必要があります：

  * [`apply_column!(::StochasticStyle, w, H, address, value)`](@ref)
  * [`step_stats(::StochasticStyle)`](@ref)

オプションとして、

  * [`CompressionStrategy(::StochasticStyle)`](@ref) を消滅後のベクトル圧縮に使用します。

[`StochasticStyles`](@ref Main.StochasticStyles)、[`Interfaces`](@ref) も参照してください。
