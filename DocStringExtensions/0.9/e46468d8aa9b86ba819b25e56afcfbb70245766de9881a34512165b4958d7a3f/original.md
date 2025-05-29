An [`Abbreviation`](@ref) for including a list of all the methods that match a documented `Method`, `Function`, or `DataType` within the current module.

# Examples

The generated markdown text will look similar to the following example where a function `f` defines two different methods (one that takes a number, and the other a string):

````markdown
```julia
f(num)
```

defined at [`<path>:<line>`](<github-url>).

```julia
f(str)
```

defined at [`<path>:<line>`](<github-url>).
````
