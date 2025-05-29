```
ref(p::Union{ArbPoly,ArbSeries,AcbPoly,AcbSeries}, i)
```

Similar to `p[i]` but instead of an `Arb` or `Acb` returns an `ArbRef` or `AcbRef` which shares the memory with the `i`-th coefficient of `p`.

!!! note
    Using `ref` for reading coefficients is always safe, but if the coefficient is mutated then care has to be taken. See the comment further down for how to handle mutation.


It only allows accessing coefficients that are allocated. For `ArbPoly` and `AcbPoly` this is typically all coefficients up to the degree of the polynomial, but can be higher if for example `Arblib.fit_length!` is used. For `ArbSeries` and `AcbSeries` all coefficients up to the degree of the series are guaranteed to be allocated, even if the underlying polynomial has a lower degree.

If the coefficient is mutated in a way that the degree of the polynomial changes then one needs to also update the internally stored length of the polynomial.

  * If the new degree is the same or lower this can be achieved with

    ```
    Arblib.normalise!(p)
    ```
  * If the new degree is higher you need to manually set the length. This can be achieved with

    ```
    Arblib.set_length!(p, len)
    Arblib.normalise!(p)
    ```

    where `len` is one higher than (an upper bound of) the new degree.

See the extended help for more details.

# Extended help

Here is an example were the leading coefficient is mutated so that the degree is lowered.

```jldoctest
julia> p = ArbPoly([1, 2], prec = 64) # Polynomial of degree 1
1.0 + 2.0⋅x

julia> Arblib.zero!(Arblib.ref(p, 1)) # Set leading coefficient to 0
0

julia> Arblib.degree(p) # The degree is still reported as 1
1

julia> length(p) # And the length as 2
2

julia> p # Printing gives weird results
1.0 +

julia> Arblib.normalise!(p) # Normalising the polynomial updates the degree
1.0

julia> Arblib.degree(p) # This is now correct
0

julia> p # And so is printing
1.0
```

Here is an example when a coefficient above the degree is mutated.

```jldoctest
julia> q = ArbSeries([1, 2, 0], prec = 64) # Series of degree 3 with leading coefficient zero
1.0 + 2.0⋅x + 𝒪(x^3)

julia> Arblib.one!(Arblib.ref(q, 2)) # Set the leading coefficient to 1
1.0

julia> q # The leading coefficient is not picked up
1.0 + 2.0⋅x + 𝒪(x^3)

julia> Arblib.degree(q.poly) # The degree of the underlying polynomial is still 1
1

julia> Arblib.set_length!(q, 3) # After explicitly setting the length to 3 it is ok
1.0 + 2.0⋅x + 1.0⋅x^2 + 𝒪(x^3)
```
