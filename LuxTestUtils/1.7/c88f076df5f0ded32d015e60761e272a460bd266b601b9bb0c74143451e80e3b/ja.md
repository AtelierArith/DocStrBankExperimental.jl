```
@jet f(args...) call_broken=false opt_broken=false
```

関数 `f` に引数 `args...` を使って JET テストを実行します。もし `JET.jl` がコンパイルに失敗した場合、マクロは何もしません。

## キーワード引数

  * `call_broken`: test_call が壊れていることを示します。
  * `opt_broken`: test_opt が壊れていることを示します。

すべての追加引数は `JET.@test_call` と `JET.@test_opt` に転送されます。

!!! tip
    毎回 `target_modules` を指定する代わりに、[`jet_target_modules!`](@ref) を使用してグローバルターゲットモジュールを設定できます。

    ```julia
    using LuxTestUtils

    jet_target_modules!(["Lux", "LuxLib"]) # Lux と LuxLib が `@jet` を呼び出すモジュールに存在することを期待します
    ```


## 例

```jldoctest
julia> @jet sum([1, 2, 3]) target_modules=(Base, Core)
テストに合格しました

julia> @jet sum(1, 1) target_modules=(Base, Core) opt_broken=true call_broken=true
テストが壊れました
  式: #= REPL[21]:1 =# JET.@test_opt target_modules = (Base, Core) sum(1, 1)
```
