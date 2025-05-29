```
reli1(x::Real)
```

Returns the real part of the 1st order polylogarithm $\Re[\operatorname{Li}_1(x)] = -\Re[\ln(1 - z)]$ of a real number $x$ of type `Real`.

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> reli1(0.5)
0.6931471805599453

julia> reli1(BigFloat("0.5"))
0.6931471805599453094172321214581765680755001343602552541206800094933936219696955
```
