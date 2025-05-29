```
ParametricTrajectoryOptimizationProblem(
    cost,
    dynamics,
    inequality_constraints,
    state_dim,
    control_dim,
    parameter_dim,
    horizon,
)
```

与えられた問題データから `ParametricTrajectoryOptimizationProblem` を構築します：

  * `cost` は `cost(xs, us, params) -> c` として呼び出され、パラメータベクトル `params` に対して与えられた状態のシーケンス `xs` と制御入力 `us` の目的値を計算します。
  * `dynamics` は `dynamics(x, u, t [, params]) -> xp` として呼び出され、前の状態 `x`、制御 `u`、時間 `t` およびオプションのパラメータ `params` から次の状態 `xp` を生成します。オプションのパラメータベクトルを切り替えるには `parameterize_dynamics` を参照してください。
  * `inequality_constraints` は `inequality_constraints(xs, us, params) -> gs` として呼び出され、状態 `xs` と `us` から制約のベクトル `gs` を生成します。ここで、`xs` と `us` のレイアウトとタイプは `cost` と同じです。この形式で指定された制約は `0 <= gs` として強制されます。すなわち、実行可能な軌道は非負の制約を評価します。問題に不等式制約がない場合は、`inequality_constraints = (xs, us, params) -> Symbolics.Num[]` と設定してください。
  * `state_dim::Integer` は状態の段階ごとの次元です。
  * `control_dim::Integer` は制御入力の段階ごとの次元です。
  * `horizon::Integer` は問題のホライズンです。
  * `parameterize_dynamics` は、ダイナミクスに渡されるオプションの `params` 引数を制御します。このフラグはデフォルトで無効です。`true` に設定すると、`dynamics` は `dynamics(x, u, t, params)` として呼び出されます。

`dynamics(x, u, t)` の代わりに。すべてのパラメータがダイナミクス呼び出しに渡されることに注意してください。

# 注意

この関数は、パラメトリック軌道最適化問題を解決するために必要なすべての関数、勾配、ヤコビ行列、およびヘッセ行列をコンパイルするために `Symbolics.jl` を使用します。したがって、上記のすべての呼び出し可能な関数は、`Symbolics.Num` 値の引数を受け入れるのに十分に一般的でなければなりません。

セットアップ手順にはコード生成が含まれるため、このコンストラクタへの呼び出しはかなり高価であり、厳密な内部ループでは避けるべきです。それに対して、異なるパラメータ値に対して同じ `ParametricTrajectoryOptimizationProblem` に対する繰り返しソルバー呼び出しは非常に高速です。したがって、再構築を避けるパラメータ化を選択することが良いアイデアです。

さらに、*全体* のパラメータベクトルが `costs`、`dynamics`、および `inequality_constraints` に渡されることに注意してください。これにより、複数の呼び出し間でパラメータを共有できます。たとえば、衝突回避半径を制御するパラメータは、コストと制約の両方に現れる可能性があります。各呼び出しのために必要なパラメータを抽出するために、`params` ベクトルに正しくインデックスを付けるのはユーザーの責任です。

# 例

以下に、2つの状態、2つの入力を持つ2Dインテグレーターのためのパラメトリック最適化問題を構築します。さらに、この問題は状態と入力に±0.1のボックス制約を特徴としています。

```@example running_example
horizon = 10
state_dim = 2
control_dim = 2
cost = (xs, us, params) -> sum(sum((x - params).^2) + sum(u.^2) for (x, u) in zip(xs, us))
dynamics = (x, u, t) -> x + u
inequality_constraints = let
    state_constraints = state -> [state .+ 0.1; -state .+ 0.1]
    control_constraints = control -> [control .+ 0.1; -control .+ 0.1]
    (xs, us, params) -> [
        mapreduce(state_constraints, vcat, xs)
        mapreduce(control_constraints, vcat, us)
    ]
end

problem = ParametricTrajectoryOptimizationProblem(
    cost,
    dynamics,
    inequality_constraints,
    state_dim,
    control_dim,
    horizon
)
```
