```
arc(place::Place, transition::Transition, type::Symbol)
```

ペトリネットにおいて、プレースとトランジションを結ぶArc型のオブジェクトを作成します。注意: 許可されるアークは次のいずれかです: :in, :read, :inout, :out, :out_many

# 例

```julia-repl
julia> p1 = place("place1", "input_place")
Place "place1" created.


julia> t1 = transition("transition1")
Transition "transition1" created.


julia> arc(p1, t1, :in)
An arc of type "in", connecting the place: place1 to the transition: transition1.

```

関連項目は [`place`](@ref), [`transition`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref) です。
