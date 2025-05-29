```
plotlylightq(p, xs=(-Inf, Inf), ys=(-Inf, Inf);
             label="", hint="", explanation="",
             correct_answer=nothing)
```

From a plotly graph of a function present a question about the `x-y` point on a graph shown on hover. (For figures with multiple graphs, the hover of the first one is taken. For parameterized plots, the hover may be computed in an unexpected manner.)

By default, correct answers select a value on the graph with `x` in the range specified by `xs` and `y` in the range specified by `ys`.

  * `xs`: specifies interval for selected point `[x₀,x₁]`, defaults to `(-Inf,Inf)`
  * `ys`: range `[y₀,y₁]`
  * `correct_answer`: When specified, allows more advanced notions of correct. This is a JavaScript code snippet with `x` and `y` representing the hovered point on the graph that is highlighted on clicking.

## Examples

```
using PlotlyLight
xs = range(0, 2pi, length=100)
ys = sin.(xs)
p = Plot(Config(x=xs, y=ys))
plotlylightq(p, (3,Inf); label="Click a value with ``x>3``")
```

An example where the default grading script needs modification. Note also, the `x`, `y` values refer to the *first* graph. (One could modify their definition in `correct answer`; they are found through `x=e.points[0].x`, `y=e.points[0].y`.)

```
xs = range(0, 2pi, length=100)
ys = sin.(xs)
p = Plot(Config(x=xs, y=ys));
push!(p.data, Config(x=xs, y=cos.(xs)));  # add layer
question = "Click a value where `sin(x)` is increasing"
# evalute pi/2 as no pi in JavaScript, also Inf -> Infinity
correct_answer = "((x >= 0 && x <= 1.5707963267948966) || (x >= 4.71238898038469 && x <= 6.283185307179586))"
plotlylightq(p; label=question, correct_answer=correct_answer)
```

!!! note
    The use of `PlotlyLight` graphics works with `Weave` and `Pluto`, but is unusable from `quarto` and `Documenter`.

