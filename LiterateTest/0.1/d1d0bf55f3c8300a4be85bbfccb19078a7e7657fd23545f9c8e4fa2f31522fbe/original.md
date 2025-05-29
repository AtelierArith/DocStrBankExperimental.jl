```
@evaltest "$code" begin $tests end
@evaltest raw"$code" begin $tests end
```

Evaluate `code`, assign it to the variable `ans`, and then run `tests`.

This macro is meant to be processed by `LiterateTest.preprocess`.
