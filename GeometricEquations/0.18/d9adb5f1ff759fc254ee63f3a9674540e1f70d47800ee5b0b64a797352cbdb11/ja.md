EquationProblem: ジオメトリック方程式と初期条件、パラメータ、時間範囲、時間ステップサイズを格納します。

### パラメータ

  * `ST <: GeometricEquation`: ディスパッチに使用されるスーパタイプ
  * `DT <: Number`: データ型
  * `TT <: Real`: 時間ステップ型
  * `AT <: AbstractArray{DT}`: 状態変数の配列型
  * `equType <: GeometricEquation`: 方程式型
  * `functionsType <: NamedTuple`: すべての関数メソッドの型
  * `solutionsType <: NamedTuple`: すべての解法メソッドの型
  * `icsType <: NamedTuple`: すべての初期条件の型
  * `parType <: OptionalParameters`: パラメータ型

### フィールド

  * `equation`: ベクトルフィールドなどを保持する親方程式オブジェクトへの参照
  * `functions`: 問題を定義するすべてのベクトルフィールドなどのメソッド
  * `solutions`: 定義されている場合、すべての解法などのメソッド
  * `tspan`: 問題の時間範囲 `(t₀,t₁)`
  * `tstep`: シミュレーションで使用される時間ステップ
  * `ics`: 初期条件を含む `NamedTuple`、各状態変数のためのフィールドを1つ含む必要があります
  * `parameters`: 方程式のパラメータを含む `NamedTuple` または、方程式にパラメータがないことを示す `NullParameters`

### サブタイプ

`EquationProblem` 型には、さまざまな方程式型のためのサブタイプがあり、例えば次のように定義されます。

```julia
const ODEProblem = EquationProblem{ODE}
```

そして、方程式と対応する問題を1ステップで構築するための便利なコンストラクタを提供します。例えば、

```julia
ODEProblem(v, tspan, tstep, ics::NamedTuple; kwargs...)
ODEProblem(v, tspan, tstep, q₀::StateVariable; kwargs...)
```

すべての問題サブタイプは、次のキーワード引数を受け取ります。

  * `invariants = NullInvariants()`
  * `parameters = NullParameters()`
  * `periodicity = NullPeriodicity()`

対応する Null 型に設定されていない場合、ユーザーは次の値を持つ `NamedTuple` を渡す必要があります。

  * 不変量のための関数、
  * パラメータのための任意のデータ構造、
  * 周期性のための解と同じデータ構造。

後者は、周期的なコンポーネントを除いて、すべての場所でゼロであるべきです。すなわち、その値が範囲 `(0, max)` 内に留まることが期待されるコンポーネントです。ゼロ以外の値で始まる範囲のサポートは現在欠けていますが、需要が生じれば追加可能です。
