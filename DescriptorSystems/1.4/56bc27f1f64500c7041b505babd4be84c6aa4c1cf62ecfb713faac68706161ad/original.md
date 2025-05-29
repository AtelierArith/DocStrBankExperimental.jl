```
sys = rdss(n, p, m; id = [ ], disc = false, Ts, T = Float64, stable = false, nfuc = 0, iduc = [ ], 
           nfuo = 0, iduo = [ ], randlt = true, randrt = true)
```

Generate a randomized descriptor state-space system `sys = (A-λE,B,C,D)` with `p` outputs and `m` inputs, with all matrices  randomly generated of type `T`.  The resulting `sys` is a continuous-time system if `disc = false` and a discrete-time system if `disc = true`.  For a discrete-time system a sample time `Δ` can be specified using the keyword argument `Ts = Δ` (default: `Δ = -1`, i.e., not specified).

If the vector `id` is nonempty, then `id[i]` specifies the order of the `i`-th infinite elementary divisor of the resulting pencil `A-λE`, which thus has `n` finite eigenvalues and `ni = sum(id)` infinite eigenvalues which are controllable and observable.  If `nfuc+nfuo > 0`, the system `sys` is non-minimal, with `A` having `nfuc` uncontrollable and `nfuo` unobservable finite eigenvalues.  If the vector `iduc` is a nonempty, then `iduc[i]` specifies the order of the `i`-th infinite elementary divisor  with uncontrollable infinite eigenvalues of the resulting pencil `A-λE`, which thus has `niuc = sum(iduc)` uncontrollable infinite eigenvalues.  If the vector `iduo` is a nonempty, then `iduo[i]` specifies the order of the `i`-th infinite elementary divisor with  unobservable infinite eigenvalues of the resulting pencil `A-λE`, which thus has `niuo = sum(iduo)` unobservable infinite eigenvalues.  If `niuc+niuo > 0`, the system `sys` is non-minimal, with `A` having `niuc` uncontrollable and `niuo` unobservable infinite eigenvalues. 

It follows, that the resulting pencil `A-λE` has  `n+nfuc+nfuo` finite eigenvalues and `ni+niuc+niuo` infinite eigenvalues.  If `stable = true`, the proper part of the system `sys` is stable, with `A` having all finite eigenvalues with negative real parts  for a continuous-time system, or with moduli less than one for a discrete-time system. 

If  `randlt = true`, a randomly generated orthogonal or unitary transformation is additionally applied to `A`, `E`, and `B` from the left.     If  `randrt = true`, a randomly generated orthogonal or unitary transformation is additionally applied to `A`, `E`,  and `C` from the right.     If `randlt = false` and `randrt = false`, the system matrices `A`, `E`, `B`, and `C` result in block stuctured forms exhibitting the  uncontrollable and unobservable finite and infinite eigenvalues of `A-λE`:

```
A-λE = diag(A1-λE1, A2-λE2, A3-λE3, A4-λE4, A5-λE5, A6-λE6),  
B = [B1; B2; 0; 0; B5; B6 ], 
C = [C1 C2 C3 C4 0 0]
```

with the diagonal blocks `A1`, `A2`, `A3`, `A4`, `A5`, `A6` of orders `n`, `ni`, `nfuc`, `niuc`, `nfuo` and `niuo`, respectively. 
