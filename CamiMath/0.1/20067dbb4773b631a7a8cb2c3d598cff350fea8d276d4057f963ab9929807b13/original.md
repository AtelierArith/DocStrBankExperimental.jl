```
bernoulliB(n::Integer [; arr=false [, msg=true]])
```

Bernoulli numbers of index `n` are defined by the recurrence relation

$$
    B_n = - \frac{1}{n+1}\sum_{k=0}^{n-1}\frac{(n+1)!}{k!(n+1-k)}B_k,
$$

with $B_0=1$ and $B_1=-1/2$. Including $B_0$ results in the *even index  convention* $(B_{2n+1}=0$ for $n>1)$.

  * `arr` : output in array format
  * `msg` : integer-overflow protection (IOP) - warning on activation

#### Examples:

```
julia> o = [bernoulliB(n) for n=0:5]; println(o)
Rational{Int64}[1//1, -1//2, 1//6, 0//1, -1//30, 0//1]

julia> o = bernoulliB(5; arr=true); println(o)
Rational{Int64}[1//1, -1//2, 1//6, 0//1, -1//30, 0//1]

julia> o = bernoulliB(big(5); arr=true); println(o)
Rational{BigInt}[1//1, -1//2, 1//6, 0//1, -1//30, 0//1]

julia> bernoulliB(60)
IOP capture: bernoulliB(60) converted to Rational{BigInt}
-1215233140483755572040304994079820246041491//56786730

julia> n = 60;
julia> bernoulliB(n; msg=false) == bernoulliB(n; msg=false, arr=true)[end]             
true
```
