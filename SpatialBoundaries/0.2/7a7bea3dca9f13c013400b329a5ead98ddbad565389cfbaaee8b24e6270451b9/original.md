```
boundaries(W::Womble, t=0.1; ignorezero=false)
```

Extracts candidate boundaries using calculated wombling object `W` on specified threshold `t`. Default threshold is 0.1, meaning that the top 10% of pixels are selected as part of the boundaries. This function returns a list of indices identifying which simplices are part of the boundaries. The NaN values in the rates of change are not going to be a part of the boundaries. The keyword `ignorezero`, which defaults to `false`, can be used to remove the points with a rate of change of 0.
