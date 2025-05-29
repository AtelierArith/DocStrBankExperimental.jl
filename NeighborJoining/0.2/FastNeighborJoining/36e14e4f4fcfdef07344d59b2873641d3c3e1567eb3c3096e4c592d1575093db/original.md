```
fastNJ(d::AbstractMatrix{<:Number})
```

fastNJ algorithm finds k independent pairs to merge and merges them for each iteration.  This is significantly faster because it is not recalculating the full pairwise Q for each pair joined.

This algorithm is nearly additive, but there are instances where the topology  '(a,(b,(c,d)))' is inferred as '((a,b), (c,d))'. This happens when  'b' is not as close to 'c' or 'd' as it is to 'a',  but 'b' is closer to the common ancestor '(c,d)' than it is to 'a'.

args:

  * d is an n by n square symetric distance matrix

returns:

  * NJClust struct with fields merges and heights

```@jldoctest
julia> d = [
           0  5  9  9 8
           5  0 10 10 9
           9 10  0  8 7
           9 10  8  0 3
           8  9  7  3 0
       ];

julia> njclusts = fastNJ(d)
NJClust{Int64, Float64}([-2 -1; -5 -4; 1 -3; 3 2], [3.0 2.0; 1.0 2.0; 3.0 4.0; 1.0 1.0])

julia> nwstring = newickstring(njclusts)
"(5:5.000000e-01,(4:2.000000e+00,(3:4.000000e+00,(2:3.000000e+00,1:2.000000e+00):3.000000e+00):2.000000e+00):5.000000e-01):0.000000e+00;"
```
