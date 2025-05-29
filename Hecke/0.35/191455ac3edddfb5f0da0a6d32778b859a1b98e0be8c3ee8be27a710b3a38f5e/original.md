```
has_preimage_with_preimage(f::MultTableGroupHom, g::MultTableGroupElem) -> (b::Bool, h::MultTableGroupElem)
```

Returns whether $g$ has a preimage under $f$. If so, the second return value is an element $h$ with $f(h) = g$.
