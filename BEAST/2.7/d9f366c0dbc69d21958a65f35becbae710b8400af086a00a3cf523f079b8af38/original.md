```
quadrule(operator, test_refspace, trial_refspace, test_index, test_chart, trial_index, trial_chart, quad_data)
```

Based on the operator kernel and the test and trial elements, this function builds an object whose type and data fields specify the quadrature rule that needs to be used to accurately compute the interaction integrals. The `quad_data` object created by `quaddata` is passed to allow reuse of any precomputed data such as quadrature points and weights, geometric quantities, etc.

The type of the returned quadrature rule will help in deciding which method of `momintegrals` to dispatch to.
