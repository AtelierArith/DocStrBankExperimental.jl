```
Data
```

This module contains a collection of [`Possibility`](@ref) types, as well as some useful utility functions for constructing them.

These currently include:

  * [`Integers{T}`](@ref), for producing integer types (except `BigInt`)
  * [`Floats{F}`](@ref), for producing floating point types (except `BigFloat`)
  * [`Booleans`](@ref), for producing booleans
  * [`Pairs`](@ref), for producing pairs of values `a => b`
  * [`Vectors`](@ref), for producing `Vector`s out of `Possibility`
  * [`Dicts`](@ref), for producing `Dict`s out of a `Possibility` for keys and one for values
  * [`AsciiCharacters`](@ref), for producing `Char`s that are `isascii`
  * [`Characters`](@ref), for producing all well-formed `Char`s, including invalid Unicode
  * [`UnicodeCharacters`](@ref), for producing ALL `Char`s, including invalid and malformed Unicode
  * [`Text`](@ref), for producing `String`s from `Possibility{Char}`
  * [`SampledFrom`](@ref), for producing a value from a given collection
  * [`Satisfying`](@ref), for filtering the values a `Possibility` produces through a predicate
  * [`Map`](@ref), for mapping a function over the values a `Possibility` produces
  * [`Just`](@ref), for producing a given fixed value
  * [`OneOf`](@ref), for choosing one of a number of given `Possibility` to produce from
  * [`Bind`](@ref), for binding a function that produces `Possibility` to the output of another `Possibility`
  * [`Recursive`](@ref), for creating recursive data structures using a basecase `Possibility` and a function that layers more `Possibility` around it
  * [`WeightedNumbers`](@ref), for sampling the numbers from `1:n` by giving `n` weights
  * [`WeightedSample`](@ref), for sampling a collection while biasing that sampling by a per-element weight

as well as these utility functions:

  * `map` for creating a `Map`
  * `filter` for creating a `Satisfying`
  * `|` for creating a `OneOf`
  * `bind` for creating a `Bind`
  * `recursive` for creating a `Recursive`
  * `Floats()` for producing all of `Float16`, `Float32` and `Float64` from the same `Possibility` at once
  * `BitIntegers()` for producing all of `Base.BitIntegers` from the same `Possibility` at once
