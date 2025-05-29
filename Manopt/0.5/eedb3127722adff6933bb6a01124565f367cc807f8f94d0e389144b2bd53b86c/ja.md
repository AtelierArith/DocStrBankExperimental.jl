```
decorate_state!(s::AbstractManoptSolverState)
```

特定のデコレーターで[`AbstractManoptSolverState`](@ref)`s`を装飾します。

# オプション引数

オプション引数はデコレーターに関する必要な詳細を提供します。

  * `debug=Array{Union{Symbol,DebugAction,String,Int},1}()`: [`DebugAction`](@ref)sを表すシンボルのセット、区切りとして使用される`Strings`、およびサブサンプリング整数です。これらは、`:Iteration`内の[`DebugGroup`](@ref)として[`DebugSolverState`](@ref)デコレーター辞書に渡されます。唯一の例外は`:Stop`で、これは`:Stop`に渡されます。
  * `record=Array{Union{Symbol,RecordAction,Int},1}()`: `Symbol`sまたは[`RecordAction`](@ref)sを直接使用して記録を指定します。整数は再び、$i$番目のイテレーションのみを記録するために使用できます。
  * `return_state=false`: オプションを[`ReturnSolverState`](@ref)でラップするかどうかを示します。これは、ソルバーがオプションを返すべきであり、最小化者だけを返すべきではないことを示します。

他のキーワードは無視されます。

# 参照

[`DebugSolverState`](@ref)、[`RecordSolverState`](@ref)、[`ReturnSolverState`](@ref)
