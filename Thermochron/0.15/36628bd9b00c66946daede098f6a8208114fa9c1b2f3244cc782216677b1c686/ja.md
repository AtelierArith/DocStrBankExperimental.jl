```julia
MCMC_varkinetics(chrons::Vector{<:Chronometer}, model::NamedTuple, npoints::Int, path.agepoints::Vector, path.Tpoints::Vector, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```

マルコフ連鎖モンテカルロ時間-温度反転法を用いて、熱年代測定のクロノメーターを指定されたベクトル `chrons` の `Chronometer` オブジェクト（`ZirconHe`、`ApatiteHe`、`ApatiteFT` など）として、モデルパラメータを名前付きタプル `model` で指定し、可変拡散動力学を用います。

後方の時間-温度経路を含む `TTResult` オブジェクトと、後方の動力学パラメータを含む `KineticResult` オブジェクトを返します。

定常拡散動力学を用いたバリアントについては `MCMC` も参照してください。

## 例

```julia
tT, kinetics = MCMC_varkinetics(chrons::NamedTuple, model::NamedTuple, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```
