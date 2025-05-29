```
r = rtf(var; Ts = rts)
r = rtf('s') or r = rtf('z'; Ts = rts) 
r = rtf("s") or r = rtf("z"; Ts = rts) 
r = rtf(:s) or r = rtf(:z; Ts = rts)
```

Create the rational transfer function `r(λ) = λ`, such that `r.var` and `r.Ts` are set as follows:

```
(1) `r.var = :s` and `r.Ts = 0` if `var = 's'`, or `var = "s"` or `var = :s` ;

(2) `r.var = :z` and `r.Ts = rts` if `var = 'z'`, or `var = "z"` or `var = :z`;

(3) `r.var = var` and `r.Ts = rts` (default `rts = 0.`) otherwise.
```
