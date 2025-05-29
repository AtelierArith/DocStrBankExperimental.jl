```
automorphism_list(C::CyclotomicExt; gens::Vector{NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}}) -> Vector{NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}}
```

Computes the automorphisms of the absolute field defined by the cyclotomic extension, i.e. of `absolute_simple_field(C). It assumes that the base field is normal.`gens` must be a set of generators for the automorphism group of the base field of $C$.
