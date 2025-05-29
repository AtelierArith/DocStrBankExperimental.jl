```
nextinput(input::VaryingInput, n::Int=1)
```

Returns the first `n` elements of this input.

### Input

  * `input` – varying input
  * `n`     – (optional, default: `1`) number of desired elements

### Output

An iterator of type `Base.Iterators.Take` that represents at most the first `n` elements of this input.
