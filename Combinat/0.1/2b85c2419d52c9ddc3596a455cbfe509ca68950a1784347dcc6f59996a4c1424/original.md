`stirling1(n,k)`

the  *Stirling  numbers  of  the  first  kind*  `S₁(n,k)`  are  defined  by `S₁(0,0)=1,   S₁(n,0)=S₁(0,k)=0`   if   `n,   k!=0`   and   the  recurrence `S₁(n,k)=(n-1)S₁(n-1,k)+S₁(n-1,k-1)`.

`S₁(n,k)`  is the  number of  permutations of  `n` points  with `k` cycles. They   are   also   given   by   the   generating  function  $n!{x\choose n}=\sum_{k=0}^n(S₁(n,k) x^k)$. Note the similarity to $x^n=\sum_{k=0}^n S₂(n,k)k!{x\choose k}$ (see  `stirling2`).  Also  the  definition of `S₁` implies  `S₁(n,k)=S₂(-k,-n)` if  `n,k<0`. There  are many formulae relating Stirling  numbers of the first kind to Stirling numbers of the second kind, Bell numbers, and Binomial numbers.

```julia-repl
julia> stirling1.(4,0:4) # Knuth calls this the trademark of S₁
5-element Vector{Int64}:
  0
  6
 11
  6
  1

julia> [stirling1(n,k) for n in 0:6, k in 0:6] # similar to Pascal's triangle
7×7 Matrix{Int64}:
 1    0    0    0   0   0  0
 0    1    0    0   0   0  0
 0    1    1    0   0   0  0
 0    2    3    1   0   0  0
 0    6   11    6   1   0  0
 0   24   50   35  10   1  0
 0  120  274  225  85  15  1

julia> stirling1(50,big(10)) # give `big` second argument to avoid overflow
101623020926367490059043797119309944043405505380503665627365376
```
