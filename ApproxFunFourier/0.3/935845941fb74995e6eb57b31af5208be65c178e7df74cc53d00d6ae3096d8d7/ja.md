```
Laurent()
```

複素指数によって張られる空間

```
    1,exp(-im*θ),exp(im*θ),exp(-2im*θ),…
```

[`Fourier`](@ref)も参照してください。

---

```
Laurent(d::Domain)
```

複素指数によって張られる空間

```
    1, exp(-im * (2pi/L*θ)), exp(im * (2pi/L*θ)), exp(-2im * (2pi/L*θ)), …
```

周期 `L` を持つドメインの場合。
