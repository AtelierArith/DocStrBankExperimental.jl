```
band(cmd0::String="", arg1=nothing; width=0.0, envelope=false, kwargs...)
```

Plot a line with a symmetrical or asymmetrical band around it. If the band is not color filled then, by default, only the envelope outline is plotted.

Example: Plot the sinc function with a green band of width 0.1 (above and below the sinc line)

```
x = y = -10:0.11:10;
band(x, sin.(x)./x, width=0.1, fill="green@80", show=true)
```

or, the same but using a function

```
band(x->sin(x)/x, 10, width=0.1, fill="green@80", show=true)
```
