```
feynman_kac(𝕋, ts; f =  zeros(size(𝕋, 1)), ψ =  zeros(size(𝕋, 1)), v = zeros(size(𝕋, 1)), direction = :backward])
```

𝕋 should be a matrix  ts should be a grid of time on which to solve the PDE

With direction = :backward, returns the solution of the PDE: u(x, t[end]) = ψ(x) 0 = u*t + 𝕋u - v(x, t)u + f(x, t) Or, equivalently, in integral form,  u(x, t) = E[∫*t^T e^{-∫*t^s v(x*u) du} f(x*s)ds + ∫*t^t e^{-∫*t^T v(x*u)du} ψ(x*T)|x*t = x] (notations are from the wikipedia article for Feynman–Kac formula)

With direction = :forward, , returns the solution of the PDE: u(x, t[1]) = ψ(x) u*t = 𝕋u - v(x, t)u + f(x, t) Or, equivalently, in integral form,  u(x, t) = E[∫*0^t e^{-∫*0^s v(x*u) du} f(x*s)ds + ∫*0^t e^{-∫*0^t v(x*u)du} ψ(x*t)|x*0 = x]

The PDE is solved using Euler method with implicit time steps
