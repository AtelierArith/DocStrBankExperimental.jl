An inline number that can be changed by clicking and dragging the mouse.

# Examples

```julia
md"""
_If Alice has $(@bind a Scrubbable(20)) apples, 
and she gives $(@bind b Scrubbable(3)) apples to Bob..._
"""
```

```julia
md"""
_...then Alice has **$(a - b)** apples left._
"""
```

In the examples above, we give the **initial value** as parameter, and the reader can change it to be lower or higher.

## Custom range

Besides an initial value, a scrubbable number also has an array of possible values that can be reached. When you pass a **single number** to `Scrubbable`, this array is automatically created.

You can also **specify the array manually**:

```julia
@bind apples Scrubbable(200 : 300; default=220)
```

## Formatting

The library [`d3-format`](https://github.com/d3/d3-format) is used to format floating-point numbers. You can specify a **format string** like `".2f"` to be used to format the scrubbable value. Have a look at their [documentation](https://github.com/d3/d3-format) to see more examples.

`@bind money Scrubbable(30e6, format=".0s", prefix="€ ")`

`@bind coolness Scrubbable(0.80 : 0.01 : 1.00, format=".0%", prefix="you are 🌝 ", suffix=" cool")`
