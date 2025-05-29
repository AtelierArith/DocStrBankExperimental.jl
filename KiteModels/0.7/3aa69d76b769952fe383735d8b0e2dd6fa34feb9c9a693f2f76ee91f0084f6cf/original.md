```
residual!(res, yd, y::MVector{S, SimFloat}, s::KPS4, time) where S

N-point tether model, four points for the kite on top:
Inputs:
State vector y   = pos1,  pos2, ... , posn,  vel1,  vel2, . .., veln,  length, v_reel_out
Derivative   yd  = posd1, posd2, ..., posdn, veld1, veld2, ..., veldn, lengthd, v_reel_outd
Output:
Residual     res = res1, res2 = vel1-posd1,  ..., veld1-acc1, ..., 

Additional parameters:
s: Struct with work variables, type KPS4
S: The dimension of the state vector
```

The number of the point masses of the model N = S/6, the state of each point  is represented by two 3 element vectors.
