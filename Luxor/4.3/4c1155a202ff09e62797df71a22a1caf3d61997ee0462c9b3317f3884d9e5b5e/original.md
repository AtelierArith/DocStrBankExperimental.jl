```
barchart(values;
        boundingbox = BoundingBox(O + (-250, -120), O + (250, 120)),
        bargap=10,
        margin = 5,
        border=false,
        labels=false,
        labelfunction = (values, i, lowpos, highpos, barwidth, scaledvalue) -> begin
                label(string(values[i]), :n, highpos, offset=10)
          end,
        barfunction =  (values, i, lowpos, highpos, barwidth, scaledvalue) -> begin
            @layer begin
                setline(barwidth)
                line(lowpos, highpos, :stroke)
            end
          end)
```

Draw a barchart where each bar is the height of a value in the `values` array. The bars will be scaled to fit in a bounding box.

Text labels are drawn if the keyword `labels=true`.

# Extended help

The function returns a vector of points; each is the bottom center of a bar.

Draw a Fibonacci sequence as a barchart:

```julia
fib(n) = n > 2 ? fib(n - 1) + fib(n - 2) : 1
fibs = fib.(1:15)
@draw begin
    fontsize(12)
    barchart(fibs, labels=true)
end
```

To control the drawing of the text and bars, define functions that process the end points:

`mybarfunction(values, i, lowpos, highpos, barwidth, scaledvalue)`

`mylabelfunction(values, i, lowpos, highpos, barwidth, scaledvalue)`

and pass them like this:

```julia
barchart(vals, barfunction=mybarfunction)
barchart(vals, labelfunction=mylabelfunction)
```

```julia
function myprologfunction(values, basepoint, minbarrange, maxbarrange, barchartheight)
    @layer begin
        setline(0.2)
        for i in 0:10:maximum(values)
            rule(boxbottomcenter(basepoint) + (0, -(rescale(i, minbarrange, maxbarrange) * barchartheight)))
        end
    end
end
```
