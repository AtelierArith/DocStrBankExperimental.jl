```
writehrse(io::IO, obj, options::HrsePrintOptions)
writehrse(obj, options::HrsePrintOptions)
```

Writes the given Julia object to the given IO object as a HRSE file. The `options` argument can be used to configure the behavior of the printer. If no IO object is given, the output is written to `stdout`. Arbitrary objects are serialized using their StructTypes.StructType.

# Examples

```jldoctest
julia> using HumanReadableSExpressions

julia> hrse = [
           :alpha => [
               [1, 2, 3, 4],
               [5, 6],
               [7, 8, 9]
           ],
           :beta => (0 => 3),
           :gamma => [
               :a => 1
               :b => 2
               :c => :c
           ]
       ];

julia> writehrse(hrse, HumanReadableSExpressions.HrsePrintOptions())
alpha: 
  1 2 3 4
  5 6
  7 8 9
beta: 0: 3
gamma: 
  a: 1
  b: 2
  c: c
```

See also [`HrsePrintOptions`](@ref).
