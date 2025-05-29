```
build(config::MITgcm_config,options::String)
```

Build the model using `genmake2`, `make depend`, and `make` unless otherwise specified via `options`. The `genmake2` and `make depend` commands link all  code files, headers, etc  in the `build/` folder before `make` compiles the model.

(part of the climate model interface as specialized for `MITgcm`)
