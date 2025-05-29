```
xb,ll = smooth(pf, M, u, y, p=parameters(pf))
xb,ll = smooth(pf, xf, wf, wef, ll, M, u, y, p=parameters(pf))
```

Perform particle smoothing using forward-filtering, backward simulation. Return smoothed particles and loglikelihood. See also [`smoothed_trajs`](@ref), [`smoothed_mean`](@ref), [`smoothed_cov`](@ref)
