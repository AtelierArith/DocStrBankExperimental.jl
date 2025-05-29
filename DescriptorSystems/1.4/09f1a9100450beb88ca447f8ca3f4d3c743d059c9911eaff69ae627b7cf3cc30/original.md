```
r = rtf(f; Ts = rts, var = rvar)
```

Create the rational transfer function `r(λ) = f(λ)` with sampling time `rts` and variable name `rvar` such that: 

(1) if `f(λ)` is a rational transfer function, then `r.Ts = rts` (default `rts = f.Ts`) and `r.var = rvar` (default `rvar = f.var`);

(2) if `f(λ)` is a rational function, then `r.Ts = rts` (default `rts = 0`) and `r.var = rvar` (default `rvar = Polynomials.indeterminate(f.num)`);

(3) if `f(λ)` is a polynomial, then `r.Ts = rts` (default `rts = 0`) and `r.var = rvar` (default `rvar = Polynomials.indeterminate(f)`);

(4) if `f(λ)` is a ral or complex number, then `r.Ts = rts` (default `rts = 0`) and `r.var = rvar` (default `rvar = :s`);
