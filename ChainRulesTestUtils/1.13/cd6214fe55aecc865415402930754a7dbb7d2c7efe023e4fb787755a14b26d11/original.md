```
@maybe_inferred [Type] f(...)
```

Like `@inferred`, but does not check the return type if tests are run as part of PkgEval or if the environment variable `CHAINRULES_TEST_INFERRED` is set to `false`.
