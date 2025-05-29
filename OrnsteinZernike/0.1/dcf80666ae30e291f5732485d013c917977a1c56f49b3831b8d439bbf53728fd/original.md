CarbajalTinoko <: Closure

Implements the Carbajal-Tinoko closure $e(r;\alpha)\left[(2-y(r))e^{y(r)}-2-y(r)\right]/\left(e^{y(r)}-1\right)$ where $e(r;\alpha)=3\exp(\alpha r)$ for $\alpha <0$ and $e(r;\alpha) = 3+\alpha$ otherwise.

Example:

```julia
closure = CarbajalTinoko(0.4)
```

References:

Carbajal-Tinoco, Mauricio D. "Thermodynamically consistent integral equation for soft repulsive spheres." The Journal of chemical physics 128.18 (2008).
