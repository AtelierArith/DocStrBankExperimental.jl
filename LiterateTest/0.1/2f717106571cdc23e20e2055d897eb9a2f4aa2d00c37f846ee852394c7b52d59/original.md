```
@evaltest_throw "$code" begin $tests end
@evaltest_throw raw"$code" begin $tests end
```

Evaluate `code`, assign the exception thrown to the variable `ans`, and then run `tests`.

This macro is meant to be processed by `LiterateTest.preprocess`.
