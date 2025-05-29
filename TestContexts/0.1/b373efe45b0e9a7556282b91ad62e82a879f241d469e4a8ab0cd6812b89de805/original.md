```
SharedValue(value::Any)
```

A shared value will be used as-is by all tests. If the value is mutable, the test cases are responsible to never change it (or at least ensure the original value is restored by the end of each test).
