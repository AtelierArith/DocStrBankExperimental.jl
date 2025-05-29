```
GramSchmidt(S; orthogonalization_interval = 1) <: SpectralStrategy{S}
```

励起状態を直交化するためにグラム・シュミット法を使用します。シミュレーションでは合計 `S` のスペクトル状態が使用され、`orthogonalization_interval` ステップごとに直交化されます。

[`ProjectorMonteCarloProblem`](@ref) のキーワード引数 `spectral_strategy` と共に使用します。
