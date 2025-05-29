```
RecordGroup <: RecordAction
```

group a set of [`RecordAction`](@ref)s into one action, where the internal [`RecordAction`](@ref)s act independently, but the results can be collected in a grouped fashion, a tuple per calls of this group. The entries can be later addressed either by index or semantic Symbols

# Constructors

```
RecordGroup(g::Array{<:RecordAction, 1})
```

construct a group consisting of an Array of [`RecordAction`](@ref)s `g`,

```
RecordGroup(g, symbols)
```

# Examples

```
g1 = RecordGroup([RecordIteration(), RecordCost()])
```

A RecordGroup to record the current iteration and the cost. The cost can then be accessed using `get_record(r,2)` or `r[2]`.

```
g2 = RecordGroup([RecordIteration(), RecordCost()], Dict(:Cost => 2))
```

A RecordGroup to record the current iteration and the cost, which can then be accessed using `get_record(:Cost)` or `r[:Cost]`.

```
g3 = RecordGroup([RecordIteration(), RecordCost() => :Cost])
```

A RecordGroup identical to the previous constructor, just a little easier to use. To access all recordings of the second entry of this last `g3` you can do either `g4[2]` or `g[:Cost]`, the first one can only be accessed by `g4[1]`, since no symbol was given here.
