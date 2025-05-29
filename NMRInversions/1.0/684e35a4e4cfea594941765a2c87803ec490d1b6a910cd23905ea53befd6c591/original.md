```
mexp(seq, u, x)
```

Construct a multi-exponential function from parameters u, and evaluate it at the values x. 

The `u` vector should be of the form [a1, b1, a2, b2, ...],  where a's are the amplitudes and b's are the reciprocals of the decay constants. The length of `u` must be an even number.

Examples: 

mexp(CPMG, [a,b] , x) = a * exp.( (1/b) * x) 

mexp(CPMG, [a,b,c,d] , x) = a * exp.( (1/b) * x) + c * exp.((1/d) * x) 

mexp(CPMG, [a,b,c,d,e,f] , x) = a * exp.( (1/b) * x) + c * exp.((1/d) * x) + e * exp.((1/f) * x) 

(where a,b,c,d,e,f are all numbers) . . .
