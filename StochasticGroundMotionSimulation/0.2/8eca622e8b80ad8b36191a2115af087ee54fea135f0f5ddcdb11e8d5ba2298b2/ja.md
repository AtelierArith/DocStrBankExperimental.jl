```
corner_frequency(m::U, src::SourceParameters{S,T}) where {S<:Float64, T<:Real, U<:Real}
```

ソーススペクトルタイプに応じて、コーナー周波数成分の3タプルを計算します。デフォルトでは単一コーナーのBruneスペクトルが考慮されますが、`src.model`が`:Atkinson_Silva_2000`に等しい場合は、ダブルコーナースペクトルの成分が返されます。他のシンボルが渡された場合は、Bruneモデルが返されます。

# 例

```julia-repl
    m = 6.0
    Δσ = 100.0
    κ0 = 0.035
    fas = FASParams(Δσ, κ0)
    # 単一コーナー周波数を計算
	src.model = :Brune
    fc, tmp1, tmp2 = corner_frequency(m, src)
    # ダブルコーナー周波数を計算
	src.model = :Atkinson_Silva_2000
    fa, fb, ε = corner_frequency(m, src)
```
