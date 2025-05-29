```
StochasticStyle(v)
```

Abstract type. When called as a function it returns the native style of the generalised vector `v` that determines how simulations are to proceed.

# Usage

Concrete `StochasticStyle`s can be used for the `style` keyword argument of [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem), [`DVec`](@ref Main.DictVectors.DVec) and [`PDVec`](@ref Main.DictVectors.PDVec). The following styles are available:

  * [`IsStochasticInteger`](@ref Main.StochasticStyles.IsStochasticInteger)
  * [`IsDeterministic`](@ref Main.StochasticStyles.IsDeterministic)
  * [`IsStochasticWithThreshold`](@ref Main.StochasticStyles.IsStochasticWithThreshold)
  * [`IsDynamicSemistochastic`](@ref Main.StochasticStyles.IsDynamicSemistochastic)
  * [`StyleUnknown`](@ref Main.StochasticStyles.StyleUnknown)

# Extended Help

## Interface

When defining a new `StochasticStyle`, subtype it as `MyStyle<:StochasticStyle{T}` where `T` is the concrete value type the style is designed to work with.

For it to work with [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem), a `StochasticStyle` must define the following:

  * [`apply_column!(::StochasticStyle, w, H, address, value)`](@ref)
  * [`step_stats(::StochasticStyle)`](@ref)

and optionally

  * [`CompressionStrategy(::StochasticStyle)`](@ref) for vector compression after annihilations,

See also [`StochasticStyles`](@ref Main.StochasticStyles), [`Interfaces`](@ref).
