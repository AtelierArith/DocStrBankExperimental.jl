```
CompressionStrategy
```

The `CompressionStrategy` controls how a vector is compressed after a step.

## Default implementation:

  * [`NoCompression`](@ref): no vector compression

## Usage

A subtype of `CompressionStrategy` can be passed as a keyword argument to the constructors for some [`StochasticStyle`](@ref)s. Calling `CompressionStrategy(s::StochasticStyle)` returns a relevant subtype. The default is [`NoCompression`](@ref).

## Interface

When defining a new `CompressionStrategy`, subtype it as `MyCompressionStrategy <: CompressionStrategy` and define these methods:

  * [`compress!(s::CompressionStrategy, v)`](@ref compress!)
  * [`compress!(s::CompressionStrategy, w, v)`](@ref compress!)
  * [`step_stats(s::CompressionStrategy)`](@ref step_stats)
