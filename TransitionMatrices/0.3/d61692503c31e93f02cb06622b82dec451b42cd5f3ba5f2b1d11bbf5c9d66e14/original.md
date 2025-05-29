```
orientation_average(𝐓::AbstractTransitionMatrix{CT, N}, pₒ; Nα = 10, Nβ = 10, Nγ = 10) where {CT, N}
```

Calculate the orientation average of a transition matrix using numerical integration, given the orientation distribution function $p_o(\alpha,\beta,\gamma)$. 

$$
\langle T_{m n m^{\prime} n^{\prime}}^{p p^{\prime}}(L)\rangle = \int_0^{2\pi}\mathrm{d}\alpha\int_0^{\pi}\mathrm{d}\beta\sin\beta\int_0^{2\pi}\mathrm{d}\gamma p_o(\alpha,\beta,\gamma) T_{m n m^{\prime} n^{\prime}}^{p p^{\prime}}(L; \alpha,\beta,\gamma)
$$

Parameters:

  * `𝐓`: the T-Matrix to be orientation averaged.
  * `pₒ`: the orientation distribution function. Note that the $\sin\beta$ part is already included.
  * `Nα`: the number of points used in the numerical integration of $\alpha$. Default to 10.
  * `Nβ`: the number of points used in the numerical integration of $\beta$. Default to 10.
  * `Nγ`: the number of points used in the numerical integration of $\gamma$. Default to 10.

!!! note
    This is the fallback method and does not utilize any symmetry, so it is expected to be slow. You should use specified versions of this function, or implement your own if there is no suited version for your combination of T-Matrix and orientation distribution function.

    You may also need to test the convergence of `Nα`, `Nβ` and `Nγ` manually. If any one is too small, there will be large errors in the results.

