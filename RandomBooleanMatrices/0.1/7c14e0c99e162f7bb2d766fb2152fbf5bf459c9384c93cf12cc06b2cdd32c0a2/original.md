```
matrixrandomizer(m [,rng]; method = curveball)
```

Create a matrix generator function that will return a random boolean matrix every time it is called, maintaining row and column sums. Non-boolean input matrix are interpreted as boolean, where values != 0 are `true`.

# Examples

``` m = rand(0:4, 5, 6) rmg = matrixrandomizer(m)

random1 = rand(rmg) random2 = rand(rmg) ``
