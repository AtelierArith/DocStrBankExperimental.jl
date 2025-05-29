```
 gradient_descent!(UDE, kwargs ...)
```

Minimizes the loss function of the `UDE` model with the gradient descent algorithm with a step size of `step_size` and a maximum number of iterations of `maxiter`. Prints the value of the loss function after each iteration when `maxiter` is true.

# kwargs

  * `step_size`: Step size for ADAM optimizer. Default is `0.05`.
  * `maxiter`: Maximum number of iterations in gradient descent algorithm. Default is `500`.
  * `verbose`: Should the training loss values be printed? Default is `false`.

```

```
