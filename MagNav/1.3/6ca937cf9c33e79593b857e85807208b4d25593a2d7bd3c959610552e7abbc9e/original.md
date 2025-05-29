```
plot_correlation_matrix(x::AbstractMatrix, features::Vector{Symbol};
                        dpi::Int         = 200,
                        Nmax::Int        = 1000,
                        show_plot::Bool  = true,
                        save_plot::Bool  = false,
                        plot_png::String = "correlation_matrix.png")
```

Plot the correlation matrix for `2-5` features.

**Arguments:**

  * `x`:         `N` x `Nf` data matrix (`Nf` is number of features)
  * `features`:  length-`Nf` feature vector (including components of TL `A`, etc.)
  * `dpi`:       (optional) dots per inch (image resolution)
  * `Nmax`:      (optional) maximum number of data points plotted
  * `show_plot`: (optional) if true, show `p1`
  * `save_plot`: (optional) if true, save `p1` as `plot_png`
  * `plot_png`:  (optional) plot file name to save (`.png` extension optional)

**Returns:**

  * `p1`: plot of correlation matrix between `features`
