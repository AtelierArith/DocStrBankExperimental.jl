```
ablines(a, b; kw...)
```

or

```
ablines([a1, a2, ..., an], [b1, b2, ..., bn]; kw...)
```

or

```
ablines(D::GMTdataset; kw...)
```

Creates a straight line(s) defined by Y = a + b * X. Input can be a pair of `a,b` parameters or a vector of them, case in which multiple straight lines are plotted. Plot limits are passed through the usual `region` option in `kw` or, if missing, we plot lines in the x = [0 10] interval. The third form, when input is a `GMTdataset` type implies that this was computed with the `linearfitxy` function, which embeds the linear fit parameters in the data type attributes. All `plot` options are available via the `kw` arguments.

# Examples:

```julia-repl
ablines([1, 2, 3], [1, 1.5, 2], linecolor=[:red, :orange, :pink], linestyle=:dash, linewidth=2, show=true)
```

```julia-repl
D = linearfitxy([0.0, 0.9, 1.8, 2.6, 3.3, 4.4, 5.2, 6.1, 6.5, 7.4], [5.9, 5.4, 4.4, 4.6, 3.5, 3.7, 2.8, 2.8, 2.4, 1.5],
                 sx = 1 ./ sqrt.([1000., 1000, 500, 800, 200, 80,  60, 20, 1.8, 1]), sy=1 ./
                 sqrt.([1., 1.8, 4, 8, 20, 20, 70, 70, 100, 500]));
plot(D, linefit=true, band_ab=true, band_CI=true, ellipses=true, Vd=2)
plot!(D, linefit=true, Vd=2)
ablines!(D, Vd=2)
ablines!(0,1, Vd=2)
```
