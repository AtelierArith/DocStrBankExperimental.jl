```julia
solve(
    ocp::CTModels.Model,
    description::Symbol...;
    kwargs...
)

```

最適制御問題 `ocp` を、（オプションの）説明によって与えられた方法で解きます。利用可能な方法は `available_methods()` で確認できます。リストの上位にあるほど優先度が高くなります。キーワード引数は選択した方法に特有で、ソルバーのオプションを表します。

!!! note
    より詳しい情報については、[最適制御問題の解法に関するチュートリアル](@ref tutorial-solve)を参照してください。


# 引数

  * `ocp::OptimalControlModel`: 解くべき最適制御問題。
  * `description::Symbol...`: 問題を解くために使用する方法の説明。
  * `kwargs...`: ソルバーのオプション。

# 例

最適制御問題を解く最も簡単な方法は、引数なしで関数を呼び出すことです。

```julia-rep
julia> sol = solve(ocp)
```

方法は、説明をシンボルとして渡すことで指定できます。部分的な説明を提供することができ、関数は最適な一致を見つけます。

```julia-rep
julia> sol = solve(ocp, :direct)
```

方法は、シンボルのリストとして完全な説明を渡すことで指定できます。

```julia-repl
julia> sol = solve(ocp, :direct, :adnlp, :ipopt)
```

キーワード引数は選択した方法に特有で、ソルバーのオプションを表します。例えば、キーワード `display` はソルバーの情報を表示するために使用されます。デフォルト値は `true` です。

```julia-rep
julia> sol = solve(ocp, :direct, :ipopt, display=false)
```

初期推定はキーワード `init` で提供できます。状態、制御、および変数の初期推定を提供できます。

```julia-rep
julia> sol = solve(ocp, init=(state=[-0.5, 0.2], control=0.5))
```

!!! tip
    初期推定の提供方法についての詳細は、[初期推定に関するチュートリアル](@ref tutorial-initial-guess)を参照してください。

