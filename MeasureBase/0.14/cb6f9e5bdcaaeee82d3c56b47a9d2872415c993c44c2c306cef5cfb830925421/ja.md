```
struct SuperpositionMeasure{NT} <: AbstractMeasure
    components :: NT
end
```

測度の重ね合わせは混合分布に類似していますが（測度は正規化される必要がないため）、スケーリングは必要ありません。二つの測度 μ と ν の重ね合わせは、より簡潔に μ + ν と書くことができます。重ね合わせ測度は次の条件を満たします。

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
