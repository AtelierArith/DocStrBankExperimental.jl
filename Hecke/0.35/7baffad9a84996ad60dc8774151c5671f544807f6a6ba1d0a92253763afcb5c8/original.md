```
is_subfield(K::KummerExt, L::KummerExt) -> Bool, Vector{Tuple{AbsSimpleNumFieldElem, Vector{Int}}}
```

Given two kummer extensions of a base field $k$, returns true and the data to define an injection from $K$ to $L$ if $K$ is a subfield of $L$. Otherwise the function returns false and some meaningless data.
