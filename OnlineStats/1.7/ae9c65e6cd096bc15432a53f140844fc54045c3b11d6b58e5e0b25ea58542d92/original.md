```
FitMultinomial(p)
```

Online parameter estimate of a Multinomial distribution.  The sum of counts does not need to be consistent across observations.  Therefore, the `n` parameter of the Multinomial distribution is returned as 1.

# Example

```
x = [1 2 3; 4 8 12]
fit!(FitMultinomial(3), x)
```
