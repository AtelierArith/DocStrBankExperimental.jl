```
register_autoloads(autoloads::Vector{Pair{Vector{String}, Expr}})
register_autoloads([
    [trigger1, trigger2, ...]   => expr1,
    [trigger10, trigger11, ...] => expr2,
    ...
])
```

REPLの入力でトリガーが見つかったときに実行される式を登録します。

各`trigger`は`String`でなければなりません。`trigger`がREPLへの入力式の中でシンボル（例：変数、関数、またはマクロ名）として見つかった場合、対応する`expr`が評価されます。各`expr`は`Expr`でなければならず、`Main.eval(expr)`で評価されます。等価性に基づいて各ユニークな`expr`は最大1回だけ評価されます。

この関数は`~/.julia/config/startup.jl`（またはあなたのstartup.jlファイルが保存されている場所）から呼び出すことを意図していますが、REPLから呼び出しても動作します。

# 例

```julia
if isinteractive()
    import BasicAutoloads
    BasicAutoloads.register_autoloads([
        ["@b", "@be"]            => :(using Chairmarks),
        ["@benchmark"]           => :(using BenchmarkTools),
        ["@test", "@testset", "@test_broken", "@test_deprecated", "@test_logs",
        "@test_nowarn", "@test_skip", "@test_throws", "@test_warn", "@inferred"] =>
                                    :(using Test),
        ["@about"]               => :(using About; macro about(x) Expr(:call, About.about, x) end),
    ])
end
```
