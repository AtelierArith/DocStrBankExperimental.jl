```
Index(hilb::HilbertSpace,name::Symbol,range::Union{Int64,Sym},aon::Int)
```

Defines an index, using a Symbol as a name, and a [`HilbertSpace`](@ref) for computation and commutator-relations. Indices with all same fields will be considered equal. See also: [`IndexedOperator`](@ref) and [`IndexedVariable`](@ref)

# Fields:

  * hilb: The whole [`HilbertSpace`](@ref), the index will be defined on.
  * name: A Symbol, which defines the name of the index, and how product-terms of [`IndexedOperator`](@ref) are ordered (alphabetical)
  * range: The upper bound limit of the index. This can be a SymbolicUitls.Symbolic or any Number.
  * aon: Number specifying the specific [`HilbertSpace`](@ref), where the Index acts on.
