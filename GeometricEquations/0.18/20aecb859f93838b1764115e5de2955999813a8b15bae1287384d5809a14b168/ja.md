`DELEEnsemble`: 離散オイラー・ラグランジュ方程式アンサンブル

離散オイラー・ラグランジュ方程式は、次の形の初期値問題を定義します。

$$
D_1 L_d (q_{n}, q_{n+1}) + D_2 L_d (q_{n-1}, q_{n}) = 0 ,
$$

ここで、離散ラグランジアンは $L_d$ です。

動的変数 $q$ は $\mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
DELEEnsemble(Ld, D1Ld, D2Ld, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
DELEEnsemble(Ld, D1Ld, D2Ld, tspan, tstep, q₀::AbstractVector{<: StateVariable}, q₁::AbstractVector{<: StateVariable}; kwargs...)
DELEEnsemble(Ld, D1Ld, D2Ld, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, q₁::AbstractVector{<: AbstractArray}; kwargs...)
```

ここで、`Ld` は離散ラグランジアンを計算する関数、`D1Ld` と `D2Ld` はそれぞれ最初と二番目の引数に関する `Ld` の導関数を計算する関数、`tspan` は問題を解くための時間区間 `(t₀,t₁)`、`tstep` はシミュレーションで使用する時間ステップ、`ics` は `NamedTuple` のエントリ `q₀` と `q₁` を持つ `AbstractVector` です。初期条件 `q₀` と `q₁` は、`StateVariable` または `AbstractArray{<:Number}` の二つの `AbstractVector` としても指定できます。関数 `Ld`、`D1Ld` および `D2Ld` のインターフェースについては、[`DELE`](@ref) を参照してください。

可能なキーワード引数については、[`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) のサブタイプに関するドキュメントを参照してください。
