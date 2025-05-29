```
sigmoid_blend(fx::Tuple, xt::Tuple, x, hardness=50)
```

Smoothly transitions the results of the functions in `fx` using the sigmoid function, with the transition between the functions at the locations in `xt`. `hardness` controls the sharpness of the transition between the functions.
