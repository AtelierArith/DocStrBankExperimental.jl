```
OneHot(col; categ=false)
```

Transforms categorical column `col` into one-hot columns of levels returned by the `levels` function of CategoricalArrays.jl. The `categ` option can be used to convert resulting columns to categorical arrays as opposed to boolean vectors.

# Examples

```julia
OneHot(1)
OneHot(:a)
OneHot("a")
OneHot("a", categ=true)
```
