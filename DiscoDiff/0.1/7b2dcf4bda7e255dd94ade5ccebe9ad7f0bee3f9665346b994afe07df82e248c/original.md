```
ignore_gradient(x) -> x
```

Drops the gradient in any computation. In reverse mode it uses ChainRulesCore  API. In forward mode it simply returns a new number with a zero dual.
