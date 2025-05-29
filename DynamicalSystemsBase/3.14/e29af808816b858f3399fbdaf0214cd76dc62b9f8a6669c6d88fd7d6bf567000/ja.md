```
ArbitrarySteppable <: DiscreteTimeDynamicalSystem
ArbitrarySteppable(
    model, step!, extract_state, extract_parameters, reset_model!;
    isdeterministic = true, set_state = reinit!,
)
```

任意の「モデル」によって生成された動的システムであり、1ステップのために関数 `step!(model)` を使用して*インプレース*でステップを進めることができます。モデルの状態は `extract_state(model) -> u` 関数によって抽出されます。モデルのパラメータは `extract_parameters(model) -> p` 関数によって抽出されます。システムは、`reset_model!` ユーザー提供関数を介して再初期化される可能性があり、この関数は次の呼び出しシグネチャを持たなければなりません。

```julia
reset_model!(model, u, p)
```

与えられた（潜在的に新しい）状態 `u` とパラメータコンテナ `p` は、どちらも [`reinit!`](@ref) 呼び出しの初期値にデフォルト設定されます。

`ArbitrarySteppable` は、DynamicalSystems.jl ライブラリ内で使用できる他のパッケージのモデルに対して DynamicalSystems.jl インターフェースを提供するために存在します。`ArbitrarySteppable` は、次の調整を加えた [`DynamicalSystem`](@ref) インターフェースに従います：

  * [`initial_time`](@ref) は常に 0 であり、時間はモデルが作成されてからのステップ数または最後の [`reinit!`](@ref) 呼び出しからのステップ数をカウントします。
  * [`set_state!`](@ref) はデフォルトで [`reinit!`](@ref) と同じです。そうでない場合、キーワード引数 `set_state` はモデルの状態を `u` に設定する関数 `set_state(model, u)` です。
  * キーワード `isdeterministic` は適切に設定する必要があります。これは、下流のアルゴリズムがエラーを出すべきかどうかを決定します。
