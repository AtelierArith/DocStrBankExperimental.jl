```
Laurent()
```

The space spanned by the complex exponentials

```
    1,exp(-im*θ),exp(im*θ),exp(-2im*θ),…
```

See also [`Fourier`](@ref).

---

```
Laurent(d::Domain)
```

The space spanned by the complex exponentials

```
    1, exp(-im * (2pi/L*θ)), exp(im * (2pi/L*θ)), exp(-2im * (2pi/L*θ)), …
```

for a domain with a period `L`.
