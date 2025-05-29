```
gpsample([x, ]gp::FiniteGP; samples=1, orbit=0.0, kwargs...)
```

ガウス過程 `gp` の有限射影から `x` に沿ったサンプルをプロットします。

`x` が提供されていない場合、`gp.x` に設定されます。

`orbit` キーワード引数は、類似のサンプルの多様体を視覚化するために使用できます。[^PH2013] 値は、サンプルの大円上の角度に対応する $[0, 1)$ の区間にマッピングされます。

## 属性

`MakieCore.Plot{AbstractGPsMakie.gpsample}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  color        :black
  colormap     :viridis
  colorrange   MakieCore.Automatic()
  cycle        [:color]
  inspectable  true
  linestyle    "nothing"
  linewidth    1.5
  orbit        0.0
  samples      1
```

[^PH2013]: Philipp Hennig (2013). [Animating Samples from Gaussian Distributions](http://mlss.tuebingen.mpg.de/2013/2013/Hennig_2013_Animating_Samples_from_Gaussian_Distributions.pdf). Technical Report No. 8 of the Max Planck Institute for Intelligent Systems.
