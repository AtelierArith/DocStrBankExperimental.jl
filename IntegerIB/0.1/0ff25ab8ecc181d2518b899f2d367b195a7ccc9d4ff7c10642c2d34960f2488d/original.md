```
get_y(x, algorithm = "nn")
```

Returns the corresponding context vector `y` to the data vector `x`. Several types of context are possible, and are selected by the `type` argument. type = "nn" is the next neighbor to every point of `x`. type = "an" stands for "adjacent neighbor", or the previous and next element of every element of x.
