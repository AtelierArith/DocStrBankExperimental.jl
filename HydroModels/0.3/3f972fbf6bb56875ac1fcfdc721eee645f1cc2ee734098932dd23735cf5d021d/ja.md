```
stateflux(name, eq)
```

方程式から `StateFlux` を作成します。ここで：

  * 方程式の左側は状態変数です
  * 右側には状態変数の変化のための式が含まれます
  * `name` はフラックスのオプションの名前です（最初の引数として提供）

# 例

```julia
@variables x, y, z
@parameters a, b

# 名前付きの状態フラックスを作成
flux1 = @stateflux_build :my_flux z = a*x + b*y

# 名前なしの状態フラックスを作成
flux2 = @stateflux_build z = a*x + b*y
```
