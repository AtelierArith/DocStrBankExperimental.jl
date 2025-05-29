```
gradient(Z::Array; axs::Tuple=axes(Z), smoothness=1.0)
```

Compute the gradient of field `Z`. Use `axs` to supply a tuple of point ranges for each dimension. 

The method is based on the gradient function of a Gaussian kernel: `smoothness` scales an auto-estimate of Gaussian σ, a large value will make the gradient function linear.   

`Z` can be any dimensions, but the method may be slow if `length(Z)>10³`. 

```
gradient(X::Matrix, Y::Matrix; smoothness=1.0)
```

Compute $∇g$  for $Y = g(X)$ where `X` is the position values (rows = points), and `Y` is the field values (e.g. a 1-column matrix). The points can have irregular positions. The method may be slow if `size(X, 1)>10³`. 

See [Example 3](@ref)
