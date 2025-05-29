```
log( x :: AbstractModelConfig, y :: String; fil="", msg="", prm=false)
```

Show or add a `git` commit to the `log` folder (i.e., `joinpath(x,"log")`).

1. If no keyword is provided then `y` should be a commit ID from `log(x)`
2. Keyword arguments are mutually exclusive (i.e., use only one at a time) and work like this:

  * `msg` is a non empty `String` : commit `msg` to `log/README.md` with message `y`.
  * `fil` is a non empty `String` : commit changes to file `log/$(fil)` with message `y`.   If `log/$(fil)` is unknown to git (i.e. commit errors out) then try adding `log/$(fil)` first.
  * `prm` is `true`  : add files found in `input` or `tracked_parameters/` (if any) to git log.

Example:

```
MC=run(ModelConfig(ClimateModels.RandomWalker,(NS=100,)))
MC.inputs[:NS]=200
msg="update tracked_parameters.toml (or skip if up to date)"
log(MC,msg,prm=true)
log(MC)
```
