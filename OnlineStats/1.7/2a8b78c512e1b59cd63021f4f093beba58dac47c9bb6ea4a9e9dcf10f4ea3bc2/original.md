```
LinReg()
```

Linear regression, optionally with element-wise ridge regularization.

# Example

```
x = randn(100, 5)
y = x * (1:5) + randn(100)
o = fit!(LinReg(), zip(eachrow(x),y))
coef(o)
coef(o, .1)
coef(o, [0,0,0,0,Inf])
```
