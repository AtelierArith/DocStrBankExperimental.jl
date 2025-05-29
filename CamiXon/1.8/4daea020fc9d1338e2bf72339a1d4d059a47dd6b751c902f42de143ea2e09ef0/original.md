```
getNcut(f0::T, f::Vector{T}, start::Int, stop::Int) where T<:Real
getNcut(f0::T, f::Vector{T}, itr::UnitRange) where T<:Real
```

Index corresponding to the intersection point of the discrete function $f[n]$ with the value $f_0$  in the interval `start ≤ n ≤ stop`, 

$$
    f[n_{cut}] = f_0.
$$

Condition: $f[n]$ must be monotonically increasing or decreasing on the interval `start ≤ n ≤ stop`.

NB. For a monotonically *decreasing* function $n_{cut}$ is approximated by the *largest* $n$ for which $f[n] > f_0$. For a monotonically *increasing* function  $n_{cut}$ is approximated by the *smallest* $n$ for which $f[n] > f_0$.
