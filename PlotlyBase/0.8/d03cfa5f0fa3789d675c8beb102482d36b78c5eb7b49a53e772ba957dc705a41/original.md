The `restyle!` method follows the semantics of the `Plotly.restyle` function in plotly.js. Specifically the following rules are applied when trying to set an attribute `k` to a value `v` on trace `ind`, which happens to be the `i`th trace listed in the vector of `ind`s (if `ind` is a scalar then `i` is always equal to 1)

  * if `v` is an array or a tuple (both translated to javascript arrays when

`json(v)` is called) then `p.data[ind][k]` will be set to `v[i]`. See examples below

  * if `v` is any other type (any scalar type), then `k` is set directly to `v`.

**Examples**

```julia
# set marker color on first two traces to be red
restyle!(p, [1, 2], marker_color="red")

# set marker color on trace 1 to be green and trace 2 to be red
restyle!(p, [2, 1], marker_color=["red", "green"])

# set marker color on trace 1 to be red. green is not used
restyle!(p, 1, marker_color=["red", "green"])

# set the first marker on trace 1 to red, the second marker on trace 1 to green
restyle!(p, 1, marker_color=(["red", "green"],))

# suppose p has 3 traces.
# sets marker color on trace 1 to ["red", "green"]
# sets marker color on trace 2 to "blue"
# sets marker color on trace 3 to ["red", "green"]
restyle!(p, 1:3, marker_color=(["red", "green"], "blue"))
```
