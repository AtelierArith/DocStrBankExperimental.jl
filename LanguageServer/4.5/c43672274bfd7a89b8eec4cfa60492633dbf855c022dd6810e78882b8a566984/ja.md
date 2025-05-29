```
runserver(pipe_in=stdin, pipe_out=stdout[, env_path])
```

`pipe_in` から読み込み、`pipe_out` に書き込む `LanguageServerInstance` を実行します。

`runserver` に渡すオプションは [`LanguageServerInstance`](@ref) に渡すものと同じです。`env_path` が指定されていない場合、優先順位に従って環境を選択しようとします：

1. [`ARGS`[1]](@ref): `julia` の呼び出しに渡された最初のコマンドライン引数。
2. [`pwd()`](@ref) を含む Julia プロジェクト。
3. `.julia/environments/v#.#` 内のデフォルトの Julia 環境。

# 例

次の Julia の呼び出しは `env_path` を `/home/example/repos/Example.jl` に設定します：

```sh
julia --project=/path/to/LanguageServer.jl \
  -e "using LanguageServer; runserver()" \
  /home/example/repos/Example.jl
```

もし `/home/example/repos/Example.jl/` に `Project.toml` または `JuliaProject.toml` があった場合、次の呼び出しは `env_path` を `/home/example/repos/Example.jl/` に設定します。そうでなければ、`v#.#` は呼び出されている Julia のメジャー/マイナー バージョンである `.julia/environments/v#.#` に設定されます。

```sh
julia --project=/path/to/LanguageServer.jl \
  -e "using LanguageServer; runserver()"
```
