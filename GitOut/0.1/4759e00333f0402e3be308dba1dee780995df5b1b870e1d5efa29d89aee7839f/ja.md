```julia
rungit(::Type{Base.Process}; ...) -> Any
rungit(
    ::Type{Base.Process},
    args;
    stdin,
    stdout,
    stderr,
    append,
    wait,
    verbose_debug_logs,
    kw...
) -> Any

```

[`git`](@ref)によって作成されたコマンドを実行します。

## キーワード引数

  * `stdin=devnull`: プロセスの `stdin`。
  * `stdout=devnull`: プロセスの `stdout`。
  * `stderr=nothing`: プロセスの `stdout`。 `nothing` の場合、エラーレポート用にバッファが作成され使用されます。 例えば、これを `devnull` に設定すると、エラーの `stderr` を表示しないようになります。
  * `append=false`: `stdout` または `stderr` がファイルに設定されている場合、ファイル出力がファイルに追加されるかどうかを制御します。
  * `wait=true`: プロセスが戻るまでスレッドがブロックされるべきかどうか。
  * `verbose_debug_logs=true`: `stderr=nothing` の場合、バッファを使用して `@debug` ログを作成します。

追加のキーワード引数は [`git`](@ref) に渡されます。
