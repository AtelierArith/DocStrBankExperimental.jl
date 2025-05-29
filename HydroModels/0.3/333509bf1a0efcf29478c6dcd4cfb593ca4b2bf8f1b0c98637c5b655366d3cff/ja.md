```
@hydroflux(name, eqs...)
```

方程式のセットから `HydroFlux` を作成します。ここで：

  * 方程式の左辺は出力変数です
  * 右辺には入力変数とパラメータが含まれます
  * パラメータは ModelingToolkit の `isparameter` を使用して識別されます
  * `name` はフラックスのオプションの名前です（最初の引数として提供）

# 例

```julia
@variables x, y, z
@parameters a, b

# 1つの方程式を持つ名前付きフラックスを作成
flux1 = @hydroflux :my_flux z = a*x + b*y

# 複数の方程式を持つフラックスを作成
flux2 = @hydroflux begin
    z₁ = a*x + b*y
    z₂ = x^2 + y^2
end
```
