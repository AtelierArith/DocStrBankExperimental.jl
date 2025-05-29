CarbajalTinoko <: Closure

Carbajal-Tinokoクロージャーを実装します $e(r;\alpha)\left[(2-y(r))e^{y(r)}-2-y(r)\right]/\left(e^{y(r)}-1\right)$ ここで $e(r;\alpha)=3\exp(\alpha r)$ であり、$\alpha <0$ の場合、そうでなければ $e(r;\alpha) = 3+\alpha$ です。

例:

```julia
closure = CarbajalTinoko(0.4)
```

参考文献:

Carbajal-Tinoco, Mauricio D. "Thermodynamically consistent integral equation for soft repulsive spheres." The Journal of chemical physics 128.18 (2008).
