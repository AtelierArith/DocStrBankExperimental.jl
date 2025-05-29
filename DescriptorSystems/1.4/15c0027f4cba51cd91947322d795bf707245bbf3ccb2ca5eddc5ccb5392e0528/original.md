```
sys = rss(n, p, m; disc = false, Ts, T = Float64, stable = false, nuc = 0, nuo = 0, randt = true)
```

Generate a randomized `n+nuc+nuo`-th order standard state-space system `sys = (A,B,C,D)` with `p` outputs and `m` inputs, with all matrices  randomly generated of type `T`. The resulting `sys` is a continuous-time system if `disc = false` and a discrete-time system if `disc = true`. For a discrete-time system a sample time `Δ` can be specified using the keyword argument `Ts = Δ` (default: `Δ = -1`, i.e., not specified).

If `stable = true`, the resulting system is stable, with `A` having all eigenvalues with negative real parts for a continuous-time system,  or with moduli less than one for a discrete-time system.  If `nuc+nuo > 0`, the system `sys` is non-minimal, with `A` having `nuc` uncontrollable and `nuo` unobservable eigenvalues.  If  `randt = true`, a randomly generated orthogonal or unitary similarity transformation is additionally applied.     If `randt = false`, the system matrices `A`, `B`, and `C` result in block stuctured forms exhibitting the  uncontrollable and unobservable eigenvalues of `A`:

```
A = diag(A1, A2, A3),  B = [B1; 0; B3], C = [C1 C2 0]
```

with the diagonal blocks `A1`, `A2`, `A3` of orders `n`, `nuc`, and `nuo`, respectively. 
