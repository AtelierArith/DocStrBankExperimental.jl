```
evaluate!(psum::PauliSum{TermType,NodePathProperties}, thetas)
```

Evaluate the expectation value of a Surrogate by evaluating all involved circuit nodes in the correct order. `eval_list` can be attained as the output of `gettraceevalorder()`
