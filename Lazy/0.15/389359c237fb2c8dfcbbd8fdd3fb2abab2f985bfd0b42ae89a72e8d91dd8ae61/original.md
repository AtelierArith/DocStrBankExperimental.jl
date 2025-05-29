```
@forward T.x functions...
```

Define methods for `functions` on type `T`, which call the relevant function on the field `x`.

# Example

```julia
struct Wrapper
    x
end

@forward Wrapper.x  Base.sqrt                                  # now sqrt(Wrapper(4.0)) == 2.0
@forward Wrapper.x  Base.length, Base.getindex, Base.iterate   # several forwarded functions are put in a tuple
@forward Wrapper.x (Base.length, Base.getindex, Base.iterate)  # equivalent to above
```
