```
find_optimal_lambda(frequencies, measurements;
        method="re_im_cv",
        width_coeff=0.1,
        rbf_kernel=SqExponentialKernel())
```

Suggests values for the hyperparameter `λ`` using Saccoccio et al.'s discrepancy or Re-Im-crossvalidation methods.

The function's inputs and keyword arguments are similar to the those of the `compute_DRT` function, with the exception of the `method` keyword argument, which allows users to choose between

  * `re_im_cv` : Re-Im-crossvalidation
  * `discrepancy`: minimisation of the discrepancy between the weights `θ` calculated                   using the real and imaginary parts of the impedance spectrum.
