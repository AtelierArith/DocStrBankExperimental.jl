```
reduce_window(f, arr, window)
```

Move a sliding window over the `arr` and apply `reduce(f, view(arr, shifted window...))` For instance `window = (-1:2, 3:4)` will produce an output matrix with entries:

`out[i,j] = reduce(f, arr[(i-1):(i+2), (j+3):(j+4)])`

This is equation is true semantically, but in implementation much less work will be done. Time complexity is `O(log(k) * n)` where 

  * `n` is the size of the array: `n = length(arr)`
  * `k` is the size of the window: `k = prod(length, window)`

Note `reduce_window` assumes, that `f` is associative and commutative.
