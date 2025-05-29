```
Restart(optimizer, every=100)
```

指定された反復回数（デフォルトは100）ごとに`optimizer`をリセットします。

### 例

```julia-repl
julia> f, bounds, _ = Metaheuristics.TestProblems.rastrigin();

julia> optimize(f, bounds, Restart(ECA(), every=200))
```

### カスタマイズ

再起動条件は、`restart_condition`メソッドをオーバーロードすることで更新できます：

```julia
function Metaheuristics.restart_condition(status, restart::Restart, information, options)
    st.iteration % params.every == 0
end
```
