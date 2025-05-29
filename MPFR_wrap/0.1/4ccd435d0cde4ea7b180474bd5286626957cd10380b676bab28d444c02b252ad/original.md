```
cmpabs(op1, op2)
```

Compare `|op1|` and `|op2|`. Return a positive value if `|op1|>|op2|`, zero if `|op1|=|op2|`, and a negative value if `|op1|<|op2|`. Raise a DomainError exception if one of the operands is NaN.
