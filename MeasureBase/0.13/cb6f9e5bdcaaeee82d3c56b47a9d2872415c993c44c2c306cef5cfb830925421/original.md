```
struct SuperpositionMeasure{NT} <: AbstractMeasure
    components :: NT
end
```

Superposition of measures is analogous to mixture distributions, but (because measures need not be normalized) requires no scaling. The superposition of two measures μ and ν can be more concisely written as μ + ν. Superposition measures satisfy

```
basemeasure(μ + ν) == basemeasure(μ) + basemeasure(ν)
```

$$
    \begin{aligned}\frac{\mathrm{d}(\mu+\nu)}{\mathrm{d}(\alpha+\beta)} & =\frac{f\,\mathrm{d}\alpha+g\,\mathrm{d}\beta}{\mathrm{d}\alpha+\mathrm{d}\beta}\\
     & =\frac{f\,\mathrm{d}\alpha}{\mathrm{d}\alpha+\mathrm{d}\beta}+\frac{g\,\mathrm{d}\beta}{\mathrm{d}\alpha+\mathrm{d}\beta}\\
     & =\frac{f}{1+\frac{\mathrm{d}\beta}{\mathrm{d}\alpha}}+\frac{g}{\frac{\mathrm{d}\alpha}{\mathrm{d}\beta}+1}\\
     & =\frac{f}{1+\left(\frac{\mathrm{d}\alpha}{\mathrm{d}\beta}\right)^{-1}}+\frac{g}{\frac{\mathrm{d}\alpha}{\mathrm{d}\beta}+1}\ .
    \end{aligned}
$$
