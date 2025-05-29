### Context <: AbstractContext

  * window::Component{:svg}
  * dim::Int64{Int64, Int64}
  * margin::Pair{Int64, Int64}

The `Context` can be used with `Gattino` methods in order to create and draw introspectable SVG layers with scaling functions. This constructor is  typically not called directly, instead use the `context` function. `?context`  provides a lot more information on contexts and context grouping.

##### example

```
using Gattino

# how you should probably use contexts
mycontext = context(500, 500) do con::Context
    Gattino.line!(con, [1, 2, 3], [1, 8, 4], "stroke" => "red", "stroke-width" => 2px)
end

# you (can) still do this, of course.
con = Context()
Gattino.line!(con, [5, 1, 2], [7, 34, 5], "stroke" => "red", "stroke-width" => "10")
display(con)
```

---

##### constructors

  * Context(::Component{:svg}, margin::Pair{Int64, Int64})
  * Context(width::Int64 = 1280, height::Int64 = 720, margin::Pair{Int64, Int64} = 0 => 0)
