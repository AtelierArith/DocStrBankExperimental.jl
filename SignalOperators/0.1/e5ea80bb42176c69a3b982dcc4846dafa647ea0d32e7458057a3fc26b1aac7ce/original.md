```
inflen
```

Represents an infinite length. Proper overloads are defined to handle  arithmetic and ordering for the infinite value. 

## Missing values

For the purposes of `SignalOperators` missing values are considered to be unknown, but of finite length. For example: `inflen * missing == inflen`.
