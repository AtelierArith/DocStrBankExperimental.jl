```
@destruct lhs = rhs [err_msg]
```

Destruct `rhs` into `lhs`. Similar to `@when let lhs = rhs`, but the destructed values are available in the current scope, and it throws an error if the pattern does not match.
