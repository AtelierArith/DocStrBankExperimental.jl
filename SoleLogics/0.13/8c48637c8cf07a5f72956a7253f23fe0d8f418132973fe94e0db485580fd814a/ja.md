```
abstract type Truth <: SyntaxLeaf end
```

値を表す構文葉のための抽象型 [lattice algebra](https://en.wikipedia.org/wiki/Lattice_(order))。ブール論理では、2つの [`BooleanTruth`](@ref) 値 TOP (⊤) と BOT (⊥) が使用されます。

また、[`BooleanTruth`](@ref) も参照してください。

# インターフェース

  * `syntaxstring(s::Truth; kwargs...)::String`
  * `dual(s::Truth)::Truth`
  * `hasdual(s::Truth)::Bool`
  * `istop(t::Truth)::Bool`
  * `isbot(t::Truth)::Bool`
  * `precedes(t1::Truth, t2::Truth)::Bool`
  * `truthmeet(t1::Truth, t2::Truth)::Truth`
  * `truthjoin(t1::Truth, t2::Truth)::Truth`

# 実装

[三値代数](https://en.wikipedia.org/wiki/Three-valued_logic)、すなわち、3つの真理値（上、下、*不明*）を持つ代数は、次の `Truth` 値の定義に基づくことができます：

```julia
import SoleLogics: precedes

abstract type ThreeVTruth <: Truth end

struct ThreeTop <: ThreeVTruth end
const ⫪ = ThreeTop() # ⊤ はすでに BooleanTruth のトップを示すために使用されています。
syntaxstring(::ThreeTop; kwargs...) = "⫪"

struct ThreeBot <: ThreeVTruth end
const ⫫ = ThreeBot() # ⊥ はすでに BooleanTruth のトップを示すために使用されています。
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

`precedes` は `Truth` 値間の（部分的）順序を定義するために使用されることに注意してください。

また、[`Connective`](@ref)、[`BooleanTruth`](@ref) も参照してください。
