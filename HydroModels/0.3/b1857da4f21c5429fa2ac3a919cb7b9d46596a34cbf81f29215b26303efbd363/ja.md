```
@neuralflux(eq::Expr)
```

`NeuralFlux`を次の構文を使用して作成します: `output ~ chain(inputs)`、ここで:

  * `output` は出力変数または出力変数のベクトルです
  * `~` は区切り文字です
  * `chain` はLuxニューラルネットワークチェーンです
  * `inputs` は入力変数のベクトルです

# 例

```julia
@variables x, y, z
chain = Chain(Dense(2 => 10, relu), Dense(10 => 1), name=:my_net)

# 単一出力のニューラルフラックスを作成
flux1 = @neuralflux z ~ chain([x, y])

# 複数出力のニューラルフラックスを作成
chain2 = Chain(Dense(2 => 16, relu), Dense(16 => 2), name=:multi_net)
flux2 = @neuralflux [z₁, z₂] ~ chain2([x, y])
```
