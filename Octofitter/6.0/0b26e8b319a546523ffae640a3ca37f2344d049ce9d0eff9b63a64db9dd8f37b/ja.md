```
System([derived,] priors, [images,] [propermotionanom,] planets..., name=:symbol)
```

システムのモデルを構築します。これは、事前分布のブロックで構築する必要があり、オプションで追加の派生パラメータを含めることができます。システムの `ProperMotionAnomLikelihood()` および/または `Images()` を提供することができます。最後に、惑星モデルがリストされます。`name` はシンボルでなければなりません。例えば `:HD56441` のように。
