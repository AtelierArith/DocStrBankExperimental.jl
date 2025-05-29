```
fibonacci(n::Integer [; arr=false [, msg=true]])
```

The sequence of integers,  $F_0,⋯\ F_{nmax}$, in which each element is  the sum of the two preceding ones, 

$$
    F_n = F_{n-1}+F_{n-2}.
$$

with $F_1=1$ and $F_0=0$. 

  * `arr` : output full Pascal triangle
  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Examples:

```
julia> fibonacci(92)
7540113804746346429

julia> fibonacci(93)
IOP capture: fibonaci(93) converted to BigInt
12200160415121876738

julia> o = fibonacci(10; arr=true); println(o)
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
```
