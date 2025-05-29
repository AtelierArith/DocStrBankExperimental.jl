```
filter_array_2!(array,smooth_x,smooth_t,position)
```

Filter the input array *in-place* using a moving mean. 

In the first two dimensions the window width is smooth*x and the border is treated as circular (for doubly periodic domains). In the space dimension the width is smooth*t and the border value is replicated.

This function calls under the hood the imfilter function of Images.jl 
