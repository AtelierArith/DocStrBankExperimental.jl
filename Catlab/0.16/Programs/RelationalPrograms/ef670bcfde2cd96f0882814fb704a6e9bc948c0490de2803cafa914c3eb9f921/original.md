Construct an undirected wiring diagram using relation notation.

Unlike the `@program` macro for directed wiring diagrams, this macro departs significantly from the usual semantics of the Julia programming language. Function calls with $n$ arguments are now interpreted as assertions that an $n$-ary relation holds at a particular point. For example, the composite of binary relations $R ⊆ X × Y$ and $S ⊆ Y × Z$ can be represented as an undirected wiring diagram by the macro call

```julia
@relation (x,z) where (x::X, y::Y, z::Z) begin
  R(x,y)
  S(y,z)
end
```

In general, the context in the `where` clause defines the set of junctions in the diagram and variable sharing defines the wiring of ports to junctions. If the `where` clause is omitted, the set of junctions is inferred from the variables used in the macro call.

The ports and junctions of the diagram may be typed or untyped, and the ports may be named or unnamed. Thus, four possible types of undirected wiring diagrams may be returned, with the type determined by the form of relation header:

1. Untyped, unnamed: `@relation (x,z) where (x,y,z) ...`
2. Typed, unnamed: `@relation (x,z) where (x::X, y::Y, z::Z) ...`
3. Untyped, named: `@relation (out1=x, out2=z) where (x,y,z) ...`
4. Typed, named: `@relation (out=1, out2=z) where (x::X, y::Y, z::Z) ...`

All four types of diagram are subtypes of [`RelationDiagram`](@ref).
