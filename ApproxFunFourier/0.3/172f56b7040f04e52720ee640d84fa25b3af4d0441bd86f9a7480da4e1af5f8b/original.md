```
Fourier()
```

The space spanned by the trigonemtric polynomials

```
    1, sin(θ), cos(θ), sin(2θ), cos(2θ), …
```

See also `Laurent`.

---

```
Fourier(d::Domain)
```

The space spanned by the trigonemtric polynomials

```
    1, sin(2pi/L*θ), cos(2pi/L*θ), sin(2pi/L*2θ), cos(2pi/L*2θ), …
```

for a domain with a period `L`.
