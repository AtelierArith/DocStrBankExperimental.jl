```
residual!(res, yd, y::MVector{S, SimFloat}, s::KPS3, time) where S

N-point tether model, one point kite at the top:
Inputs:
State vector y   = pos1, pos2, ..., posn, vel1, vel2, ..., veln
Derivative   yd  = vel1, vel2, ..., veln, acc1, acc2, ..., accn
Output:
Residual     res = res1, res2 = pos1,  ..., vel1, ...

Additional parameters:
s: Struct with work variables, type KPS3
S: The dimension of the state vector
```

The number of the point masses of the model N = S/6, the state of each point  is represented by two 3 element vectors.
