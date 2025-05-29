```
DebugAction
```

A `DebugAction` is a small functor to print/issue debug output. The usual call is given by `(p::AbstractManoptProblem, s::AbstractManoptSolverState, k) -> s`, where `i` is the current iterate.

By convention `i=0` is interpreted as "For Initialization only," only debug info that prints initialization reacts, `i<0` triggers updates of variables internally but does not trigger any output.

# Fields (assumed by subtypes to exist)

  * `print` method to perform the actual print. Can for example be set to a file export,

or to @info. The default is the `print` function on the default `Base.stdout`.
