```
build(config::MITgcm_config)
```

Build the model using `genmake2`, `make depend`, and `make`. The first two link all  code files, headers, etc  in the `build/` folder before compiling the model.

Note : this is skipped if `config.inputs[:setup][:main][:exe]` is specified.
