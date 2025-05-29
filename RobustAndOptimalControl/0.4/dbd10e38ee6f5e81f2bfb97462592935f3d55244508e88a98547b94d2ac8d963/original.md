```
bilineard2c(Ad::AbstractArray, Bd::AbstractArray, Cd::AbstractArray, Dd::AbstractArray, Ts::Number; tolerance=1e-12)
```

Balanced Bilinear transformation in State-Space. This method computes a continuous time equivalent of a discrete time system, such that

```
G_c(z) = z2s[G_d(z)]
```

in a manner which accomplishes the following   (i)   Preserves the infinity L-infinity norm over the transformation   (ii)  Finds a system which balances B and C, in the sense that ||B||*2=||C||*2   (iii) Satisfies G*d(z) = s2z[z2s[G*d(z)]] for some map s2z[]
