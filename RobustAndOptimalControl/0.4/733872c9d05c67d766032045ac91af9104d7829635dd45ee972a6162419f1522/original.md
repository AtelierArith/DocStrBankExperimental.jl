```
bilinearc2d(Ac::AbstractArray, Bc::AbstractArray, Cc::AbstractArray, Dc::AbstractArray, Ts::Number; tolerance=1e-12)
```

Balanced Bilinear transformation in State-Space. This method computes a discrete time equivalent of a continuous-time system, such that

$$
G_d(z) = s2z[G_c(s)]
$$

in a manner which accomplishes the following   (i)   Preserves the infinity L-infinity norm over the transformation   (ii)  Finds a system which balances B and C, in the sense that $||B||_2=||C||_2$   (iii) Satisfies $G_c(s) = z2s[s2z[G_c(s)]]$ for some map z2s[]
