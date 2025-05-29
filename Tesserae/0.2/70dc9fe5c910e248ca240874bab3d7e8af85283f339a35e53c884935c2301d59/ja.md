```
CPDI()
```

移流粒子ドメイン補間 (CPDI) のカーネル [^CPDI]。`CPDI` には、粒子プロパティに初期粒子長 `l` と変形勾配 `F` が必要です。たとえば、2次元では、プロパティは次のようになる可能性があります。

```jl
ParticleProp = @NamedTuple begin
    < variables... >
    l :: Float64
    F :: Mat{2, 2, Float64, 4}
end
```

[^CPDI]: [Sadeghirad, A., Brannon, R.M. and Burghardt, J., 2011. A convected particle domain interpolation technique to extend applicability of the material point method for problems involving massive deformations. International Journal for numerical methods in Engineering, 86(12), pp.1435-1456.](https://doi.org/10.1002/nme.3110)
