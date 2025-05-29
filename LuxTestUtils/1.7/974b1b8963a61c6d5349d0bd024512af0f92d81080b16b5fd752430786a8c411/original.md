```
@test_softfail expr
```

Evaluate `expr` and record a test result. If `expr` throws an exception, the test result will be recorded as an error. If `expr` returns a value, and it is not a boolean, the test result will be recorded as an error.

If the test result is false then the test will be recorded as a broken test, else it will be recorded as a pass.
