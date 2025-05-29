```
maximal_order(K::NumField{QQFieldElem}; discriminant::ZZRingElem, ramified_primes::Vector{ZZRingElem}) -> AbsNumFieldOrder
```

Returns the maximal order of $K$. Additional information can be supplied if they are already known, as the ramified primes or the discriminant of the maximal order.

# Example

```julia-repl
julia> Qx, x = QQ["x"];
julia> K, a = number_field(x^3 + 2, "a");
julia> O = maximal_order(K);
```
