```
target!(tc::TestCase, score::Float64)
```

Update `tc` to use `score` as the score this `TestCase` achieves during optimization.

!!! warning "Multiple Updates"
    This score can only be set once! Repeated calls will be ignored.

