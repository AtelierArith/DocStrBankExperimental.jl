```
preimage(f::Map(FPModuleHomomorphism),
         v::FPModuleElem{T}) where T <: RingElement
```

Return a preimage of $v$ under the homomorphism $f$, i.e. an element of the domain of $f$ that maps to $v$ under $f$. Note that this has no special mathematical properties. It is an element of the set theoretical preimage of the map $f$ as a map of sets, if one exists. The preimage is neither unique nor chosen in a canonical way in general. When no such element exists, an exception is raised.
