```julia
MCMC(chrons::Vector{<:Chronometer}, model::NamedTuple, npoints::Int, path.agepoints::Vector, path.Tpoints::Vector, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```

マルコフ連鎖モンテカルロ法による熱年代測定クロノメーター `chrons` の時間-温度逆転の推定。`chrons` は `Chronometer` オブジェクト（`ZirconHe`、`ApatiteHe`、`ApatiteFT` など）のベクターであり、モデルパラメータは名前付きタプル `model` で指定され、変動する拡散動力学を考慮しています。

後方時間-温度経路を含む `TTResult` オブジェクトを返します。

変動する拡散動力学を持つバリアントについては `MCMC_varkinetics` を参照してください。

## 例

```julia
tT = MCMC(chrons::NamedTuple, model::NamedTuple, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```
