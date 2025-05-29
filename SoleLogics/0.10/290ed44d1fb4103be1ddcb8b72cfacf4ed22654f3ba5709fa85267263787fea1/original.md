```
abstract type AbstractWorld end
```

Abstract type for the nodes of an annotated accessibility graph (Kripke structure). This is used, for example, in modal logic, where the truth of formulas is relativized to *worlds*, that is, nodes of a graph.

# Implementing

When implementing a new world type, the logical semantics should be defined via `accessibles` methods; refer to the help for `accessibles`.

See also [`AbstractKripkeStructure`](@ref), [`AbstractFrame`](@ref).
