```
abstract type Truth <: SyntaxLeaf end
```

値を表す構文葉のための抽象型である [lattice algebra](https://en.wikipedia.org/wiki/Lattice_(order))。ブール論理では、2つの [`BooleanTruth`](@ref) 値 TOP (⊤) と BOT (⊥) が使用されます。

関連情報として [`BooleanTruth`](@ref) を参照してください。

# 実装

3つの真理値（上、下、*不明*）を持つ代数である [three-valued algebra](https://en.wikipedia.org/wiki/Three-valued_logic) は、次の `Truth` 値の定義に基づくことができます：

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

`precedes` は `Truth` 値間の（部分的な）順序を定義するために使用されることに注意してください。

関連情報として [`Connective`](@ref)、[`BooleanTruth`](@ref) を参照してください。
