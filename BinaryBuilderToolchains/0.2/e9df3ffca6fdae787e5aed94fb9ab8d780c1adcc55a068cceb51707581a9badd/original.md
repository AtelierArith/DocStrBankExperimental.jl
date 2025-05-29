```
with_toolchains(f::Function, toolchains::Vector{AbstractToolchain};
                env::Dict{String,String} = ENV,
                deploy_dir::String = mktempdir(),
                verbose::Bool = false)
```

Call `f(prefix, env)` with the given `toolchains` deployed and ready to go within `deploy_root`.  Use this to quickley set up the given toolchains for usage with `run()` commands as follows:

```
with_toolchains(toolchains) do prefix, env
    cd(build_path) do
        run(setenv(`make install`, env))
    end
end
```

The `prefix` is given in the event that you want to do something with the deployed toolchains, however most users will not need to use it for anything. By default, the commands will inherit the current environment, set the `env` keyword argument to prevent this.  Note that a few known conflicting environment variables are automatically filtered out from the external environment, see `filter_env_vars()` for more detail.
