Decompose f in the truncated quadratic module associated to the constraints H=0, G>=0:

```
WS0, WS, P, v, M = sos_decompose(f, G, H, X, d, optimizer; exact = false, round = Inf64 )
```

such that 

$f = \sum_k \omega_{0,k} q_{0,k}^2 + \sum_j (\sum_k \omega_{j,k} q_{j,k}^2)*G[j] + \sum_i P[i]*H[i]              (+)$

where

  * f is the polynomial to decompose
  * G = [...] are the non-negativity constraints
  * H = [...] are the equality constraints
  * X is the set of variables
  * d is the order of the relaxation
  * `optimizer` (optional) is the optimizer used to solve the SDP program. The default value is `MMT[:optimizer]`
  * if `exact = true` then an exact decomposition with rational coefficients is computed.
  * if the option `round = p` is provided, then a round of at most `p`digits is used.

In the output decomposition, 

  * WS0 = [w0, Q0] where w0 is an array of weights $\omega_{0,k}$ in (+) and Q0 is an array of polynomials (q_{0,k} in (+)) of degree $\le 2d -\deg(G[i])$
  * WS = [WS1, WS2, ...] with WSi as WS0 for the weights $\omega_{j,k}$ and polynomials $q_j,k$in (+)
  * P[i] is a polynomial of degree $\le 2d - \deg(H[i])$
  * v is the maximal smallest eigenvalue of S0 such that $(X^d)^t S0 (X^d) = \sum_k \omega_{0,k} q_{0,k}^2$ in (*)
  * `M`is the JuMP optimization model
