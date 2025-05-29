```
with_toolchains(f::Function, toolchains::Vector{AbstractToolchain};
                env::Dict{String,String} = ENV,
                deploy_dir::String = mktempdir(),
                verbose::Bool = false)
```

指定された `toolchains` がデプロイされ、`deploy_root` 内で準備が整った状態で `f(prefix, env)` を呼び出します。これを使用して、次のように `run()` コマンドで使用するために指定されたツールチェーンを迅速にセットアップします。

```
with_toolchains(toolchains) do prefix, env
    cd(build_path) do
        run(setenv(`make install`, env))
    end
end
```

`prefix` はデプロイされたツールチェーンで何かを行いたい場合に指定されますが、ほとんどのユーザーはそれを何かに使用する必要はありません。デフォルトでは、コマンドは現在の環境を引き継ぎますが、これを防ぐために `env` キーワード引数を設定してください。いくつかの既知の競合する環境変数は、外部環境から自動的にフィルタリングされることに注意してください。詳細については `filter_env_vars()` を参照してください。
