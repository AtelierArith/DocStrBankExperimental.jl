```
snoop_bench(config::BotConfig, test_modul::Module = Main)
```

Benchmark your precompile files using the package's `runtests.jl` file.

During snooping, `snoop_bench` sets the global variable `SnoopCompile_ENV` to `true`. If needed, your `runtests.jl` can check for the existence and value of this variable to customize test behavior specifically for snooping. ```
