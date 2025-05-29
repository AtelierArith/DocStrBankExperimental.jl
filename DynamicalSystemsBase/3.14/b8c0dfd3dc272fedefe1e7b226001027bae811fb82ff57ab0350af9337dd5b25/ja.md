```
reinit!(ds::DynamicalSystem, u = initial_state(ds); kwargs...) → ds
```

`ds`の状態をリセットし、初期状態`u`で初期化されたかのようにします。`ds`を進化させるエコシステムのほぼすべての関数は、最初にこの関数を呼び出します。新しい状態`u`に加えて、キーワード`t0 = initial_time(ds)`および`p = current_parameters(ds)`を設定することもできます。

```
reinit!(ds::DynamicalSystem, u::AbstractDict; kwargs...) → ds
```

`u`が`AbstractDict`（[`set_state!`](@ref)で特定の状態変数を部分的に設定するため）である場合、変更はキーワード`reference_state = copy(initial_state(ds))`で与えられた状態で行われます。

```
reinit!(ds, ::Nothing; kwargs...)
```

このメソッドは何もしません。システムはそのままにされます。これは、`reinit!`を呼び出す下流の関数が、システムをリセットすることなく、正確な現在の状態から続行できるようにするためです。
