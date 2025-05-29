`diaconis_graham(m::Matrix{<:Integer}, moduli::Vector{<:Integer})`

returns the normal form defined for the set of generators defined by `m` of the  abelian group defined by `moduli`. in P. Diaconis and R. Graham., "The graph  of generating sets  of an abelian  group", Colloq. Math., 80:31–38,

1999. 

`moduli`  should  have  positive  entries  such  that `moduli[i+1]` divides `moduli[i]` for all `i`, representing the abelian group `A=ℤ/moduli[1]×…×ℤ/moduli[n]`, where `n=length(moduli)`.

`m`  should have `n` columns, and each  line, with the `i`-th element taken `mod  moduli[i]`, represents  an element  of `A`;  the set  of rows  of `m` should generate `A`.

The  function returns  'nothing' if  the rows  of `m`  do not generate `A`. Otherwise it returns a named tuple `r` with fields

`r.normal`:  the Diaconis-Graham normal form, a matrix of same shape as `m` where  either the first `n` rows are  the identity matrix and the remaining rows  are `0`,  or `length(m)=n`  and `.normal`  differs from  the identity matrix only in the entry `.normal[n,n]`, which is prime to `moduli[n]`.

`r.rowtrans`: unimodular matrix such that `r.normal==mod.(r.rowtrans*m,moduli')`

Here is an example:

```julia-repl
julia> r=diaconis_graham([3 0;4 1],[10,5])
(rowtrans = [-13 10; 4 -3], normal = [1 0; 0 2])

julia> r.normal==mod.(r.rowtrans*[3 0;4 1],[10,5]')
true
```
