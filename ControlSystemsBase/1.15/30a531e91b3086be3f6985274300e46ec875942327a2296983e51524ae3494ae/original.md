```
sys_fr = freqresp(sys, w)
```

Evaluate the frequency response of a linear system

`w -> C*((iw*im*I - A)^-1)*B + D`

of system `sys` over the frequency vector `w`.
