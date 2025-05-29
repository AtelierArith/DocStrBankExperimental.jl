```
install_speculator(
    predicate = (m, _) -> m ∉ [Base, Core];
background::Bool = true, parameters...)
```

REPL内の各入力`value`に対して`speculate(predicate, value; background, parameters...)`を呼び出すフックをインストールします。

この関数への後続の呼び出しはフックを置き換えるために使用できます。フックは[`uninstall_speculator`](@ref)を使用して削除できます。この関数は非対話型セッションでは効果がありません。

詳細は[`speculate`](@ref)を参照してください。

!!! tip
    REPLのレイテンシを減らすために`startup.jl`ファイルでこれを使用してください。REPLが初期化されることに依存しているため、ファイルの最後に配置する必要があります。


```julia-repl
julia> install_speculator(; limit = 2, verbosity = debug)

julia> f() = nothing;

[ Info: Compiled `Main.f()`
julia> g(::Union{String, Symbol}) = nothing;

[ Info: Compiled `Main.g(::Symbol)`
[ Info: Compiled `Main.g(::String)`
```
