This module introduces modular arithmetic.

The  integer `x` mod. `n` is constructed  by the function `Mod(x,n)`. If `n isa  Int` the result is of type `Mod{UInt64}`. If `n isa BigInt` the result is  of  type  `Mod{BigInt}`.  Since  `n`  is  not  encoded in the type, the elements  `0` and `1` mod.  `n` cannot be constructed  from the type, which causes  some problems for some Julia functionality (for instance `inv` on a matrix does not work). For prime moduli `p`, the type `FFE{p}` in `FiniteFields` does not have such limitations.

Example:

```julia-repl
julia> a=Mod(5,19)
Mod{UInt64}: 5₁₉

julia> a^2
Mod{UInt64}: 6₁₉

julia> inv(a)
Mod{UInt64}: 4₁₉

julia> a*inv(a)
Mod{UInt64}: 1₁₉

julia> a+2
Mod{UInt64}: 7₁₉

julia> a*2
Mod{UInt64}: -9₁₉

julia> a+1//2
Mod{UInt64}: -4₁₉

julia> Integer(a) # get back an integer from a
5

julia> order(a) # multiplicative order of a
9
```
