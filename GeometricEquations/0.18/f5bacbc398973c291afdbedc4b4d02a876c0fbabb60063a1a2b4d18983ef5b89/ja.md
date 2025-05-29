`DELEProblem`: 離散オイラー・ラグランジュ方程式問題

離散オイラー・ラグランジュ方程式は、次の形の初期値問題を定義します。

$$
D_1 L_d (q_{n}, q_{n+1}) + D_2 L_d (q_{n-1}, q_{n}) = 0 ,
$$

ここで、$L_d$は離散ラグランジアンです。

動的変数$q$は初期条件$q_{0}$と$q_{1}$を持ち、$\mathbb{R}^{d}$の値を取ります。

### コンストラクタ

```julia
DELEProblem(Ld, D1Ld, D2Ld, tspan, tstep, ics::NamedTuple; kwargs...)
DELEProblem(Ld, D1Ld, D2Ld, tspan, tstep, q₀::StateVariable, q₁::StateVariable; kwargs...)
DELEProblem(Ld, D1Ld, D2Ld, tspan, tstep, q₀::AbstractArray, q₁::AbstractArray; kwargs...)
```

ここで、`Ld`は離散ラグランジアンを計算する関数、`D1Ld`および`D2Ld`はそれぞれ最初と二番目の引数に関する`Ld`の導関数を計算する関数、`tspan`は問題を解くための時間区間$(t₀,tₙ)$、`tstep`はシミュレーションで使用する時間ステップ、`ics`は`StateVariable`型のエントリ`q₀`と`q₁`を持つ`NamedTuple`です。初期条件`q₀`と`q₁`は、`StateVariable`または`AbstractArray{<:Number}`として直接指定することもできます。

関数`Ld`、`D1Ld`および`D2Ld`のインターフェースについては、[`DELE`](@ref)を参照してください。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem)のサブタイプに関するドキュメントを参照してください。

### 関数定義

離散ラグランジアンを提供する関数`Ld`は、次のインターフェースを持たなければなりません。

```julia
function Ld(t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    return ...
end
```

ここで、`t_{n}`と`t_{n+1}`は前のステップと次のステップの時間、`q_{n}`と`q_{n+1}`は前のステップと次のステップの解ベクトル、`params`はラグランジアンが依存する可能性のある追加のパラメータを持つ`NamedTuple`です。離散ラグランジアンの最初と二番目の引数に関する導関数、`D_1 L_d`および`D_2 L_d`は、それぞれ次のインターフェースを持たなければなりません。

```julia
function D1Ld(D, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D1[1] = ...
    D1[2] = ...
    ...
end
```

および

```julia
function D2Ld(D2, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D2[1] = ...
    D2[2] = ...
    ...
end
```
