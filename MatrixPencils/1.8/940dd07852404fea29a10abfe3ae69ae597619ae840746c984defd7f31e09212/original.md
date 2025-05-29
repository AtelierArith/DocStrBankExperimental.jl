```
 lps2ls(A, E, B, F, C, G, D, H; compacted = false, atol1 = 0, atol2 = 0, atol3 = 0, rtol = min(atol1,atol2,atol3)>0 ? 0 : n*ϵ) -> (Ad,Ed,Bd,Cd,Dd)
```

Construct an input-output equivalent descriptor system linearizations `(Ad-λdE,Bd,Cd,Dd)` to a pencil based linearization  `(A-λE,B-λF,C-λG,D-λH)` satisfying 

```
            -1                        -1
 Cd*(λEd-Ad)  *Bd + Dd = (C-λG)*(λE-A)  *(B-λF) + D-λH .
```

If `compacted = true`, a compacted linearization is determined by exploiting possible rank defficiencies of the matrices `F`, `G`, and `H`.  

The keyword arguments `atol1`, `atol2`, `atol3`, and `rtol`, specify, respectively, the absolute tolerance for the  nonzero elements of `F`, the absolute tolerance for the nonzero elements of `G`,  the absolute tolerance for the nonzero elements of `H` and the relative tolerance  for the nonzero elements of `F`, `G` and `H`. The default relative tolerance is `n*ϵ`, where `n` is the size of   `A`, and `ϵ` is the machine epsilon of the element type of `A`. 
