```
ndsparse(keys, values; kw...)
```

Construct an NDSparse array with the given `keys` and `values` columns. On construction, the keys and data are sorted in lexicographic order of the `keys`.

# Keyword Argument Options:

  * `agg = nothing` – Function to aggregate values with duplicate keys.
  * `presorted = false` – Are the key columns already sorted?
  * `copy = true` – Should the columns in `keys` and `values` be copied?
  * `chunks = nothing` – Provide an integer to distribute data into `chunks` chunks.

      * A good choice is `nworkers()` (after `using Distributed`)
      * See also: [`distribute`](@ref)

# Examples:

```
x = ndsparse(["a","b"], [3,4])
keys(x)
values(x)
x["a"]

# Dimensions are named if constructed with a named tuple of columns
x = ndsparse((index = 1:10,), rand(10))
x[1]

# Multiple dimensions by passing a (named) tuple of columns
x = ndsparse((x = 1:10, y = 1:2:20), rand(10))
x[1, 1]

# Value columns can also have names via named tuples
x = ndsparse(1:10, (x=rand(10), y=rand(10)))
```
