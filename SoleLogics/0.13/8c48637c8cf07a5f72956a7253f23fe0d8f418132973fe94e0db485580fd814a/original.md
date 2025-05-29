```
abstract type Truth <: SyntaxLeaf end
```

Abstract type for syntax leaves representing values of a [lattice algebra](https://en.wikipedia.org/wiki/Lattice_(order)). In Boolean logic, the two [`BooleanTruth`](@ref) values TOP (⊤) and BOT (⊥) are used.

See also [`BooleanTruth`](@ref).

# Interface

  * `syntaxstring(s::Truth; kwargs...)::String`
  * `dual(s::Truth)::Truth`
  * `hasdual(s::Truth)::Bool`
  * `istop(t::Truth)::Bool`
  * `isbot(t::Truth)::Bool`
  * `precedes(t1::Truth, t2::Truth)::Bool`
  * `truthmeet(t1::Truth, t2::Truth)::Truth`
  * `truthjoin(t1::Truth, t2::Truth)::Truth`

# Implementation

A [three-valued algebra](https://en.wikipedia.org/wiki/Three-valued_logic), that is, an algebra with three truth values (top, bottom and *unknown*), can be based on the following `Truth` value definitions:

```julia
import SoleLogics: precedes

abstract type ThreeVTruth <: Truth end

struct ThreeTop <: ThreeVTruth end
const ⫪ = ThreeTop() # Note that ⊤ is already use to indicate BooleanTruth's top.
syntaxstring(::ThreeTop; kwargs...) = "⫪"

struct ThreeBot <: ThreeVTruth end
const ⫫ = ThreeBot() # Note that ⊥ is already use to indicate BooleanTruth's top.
syntaxstring(::ThreeBot; kwargs...) = "⫫"

struct ThreeUnknown <: ThreeVTruth end
const υ = ThreeUnknown()
syntaxstring(::ThreeUnknown; kwargs...) = "υ"

istop(t::ThreeTop) = true
isbot(t::ThreeBot) = true

precedes(::ThreeBot, ::ThreeTop) = true
precedes(::ThreeBot, ::ThreeUnknown) = true
precedes(::ThreeUnknown, ::ThreeTop) = true
precedes(::ThreeTop, ::ThreeBot) = false
precedes(::ThreeUnknown, ::ThreeBot) = false
precedes(::ThreeTop, ::ThreeUnknown) = false
```

Note that `precedes` is used to define the (partial) order between `Truth` values.

See also [`Connective`](@ref), [`BooleanTruth`](@ref).
