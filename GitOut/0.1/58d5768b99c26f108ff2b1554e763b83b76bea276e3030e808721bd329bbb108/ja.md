```julia
git(
;
    use_system,
    adjust_PATH,
    adjust_LIBPATH,
    env,
    dir
) -> Cmd

```

`git` コマンドを `Cmd` オブジェクトとして返します。

## キーワード引数

  * `use_system`: システム git を使用するかどうか。 [`use_system_git!`](@ref) を参照してください。 これが呼び出されなかった場合、デフォルトは `false` です。
  * `adjust_PATH=false`: `Git_jll` を使用する際に `PATH` 変数を調整するかどうか。
  * `adjust_LIBPATH=true`: `Git_jll` を使用する際に `LIBPATH` 変数を調整するかどうか。
  * `env=ENV`: コマンドの環境を指定するキーと値のコレクション。 `Base.ENV` を参照してください。
  * `dir=""`: `git` コマンドを実行するディレクトリ。 これは `git` の `-C` オプションを使用します。 空の場合、`-C` 引数は渡されません。
