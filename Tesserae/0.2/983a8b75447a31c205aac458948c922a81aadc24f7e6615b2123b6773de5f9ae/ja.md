```
uGIMP()
```

変更されていない一般化補間材料点 (uGIMP) のカーネル [^GIMP]。`uGIMP` は、粒子プロパティにおける初期粒子長 `l` を次のように要求します：

```jl
ParticleProp = @NamedTuple begin
    < variables... >
    l :: Float64
end
```

[^GIMP]: [Bardenhagen, S. G., & Kober, E. M. (2004). The generalized interpolation material point method. *Computer Modeling in Engineering and Sciences*, 5(6), 477-496.](https://doi.org/10.3970/cmes.2004.005.477)
