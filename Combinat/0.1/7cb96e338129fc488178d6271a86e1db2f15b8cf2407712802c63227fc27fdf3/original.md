`stirling2(n,k)`

the  *Stirling  numbers  of  the  second  kind* are defined by `S₂(0,0)=1`, `S₂(n,0)=S₂(0,k)=0` if `n, k!=0` and `S₂(n,k)=k S₂(n-1,k)+S₂(n-1,k-1)`, and also as coefficients of the generating function $x^n=\sum_{k=0}^{n}S₂(n,k) k!{x\choose k}$.

```julia-repl
julia> stirling2.(4,0:4)  # Knuth calls this the trademark of S₂
5-element Vector{Int64}:
 0
 1
 7
 6
 1

julia> [stirling2(i,j) for i in 0:6, j in 0:6] # similar to Pascal's triangle
7×7 Matrix{Int64}:
 1  0   0   0   0   0  0 
 0  1   0   0   0   0  0
 0  1   1   0   0   0  0
 0  1   3   1   0   0  0
 0  1   7   6   1   0  0
 0  1  15  25  10   1  0
 0  1  31  90  65  15  1

julia> stirling2(50,big(10)) # give `big` second argument to avoid overflow
26154716515862881292012777396577993781727011
```
