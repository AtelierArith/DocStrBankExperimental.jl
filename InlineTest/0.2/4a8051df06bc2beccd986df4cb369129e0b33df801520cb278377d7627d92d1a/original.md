```
@testset args...
```

Similar to `Test.@testset args...`, but the contained tests are not run immediately, and are instead stored for later execution, triggered by [`retest()`](@ref) or `runtests()`.

Besides the `@testset` body (last argument) and a description string, arguments of `@testset` can be:

  * the `verbose` option, with a *literal* boolean value (e.g. `verbose=true`)
  * a literal symbol, serving as a label which can be used for testset filtering (see [`retest`](@ref)'s docstring for details). All nested testsets inherit such labels.

Invocations of `@testset` can be nested, but qualified invocations of `ReTest.@testset` can't.

Internally, `@testset` expressions are converted to an equivalent of `Test.@testset` at execution time.
