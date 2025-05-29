```julia
# single-line:
TextField(default="", placeholder=nothing)

# with specified size:
TextField(size; default="", placeholder=nothing)
```

A text input - the user can type text, the text is returned as `String` via `@bind`.

# Keyword arguments

  * `default`: the initial value
  * `placeholder`: a value to display when the text input is empty

# `size` argument

  * If `size` is a tuple `(cols::Integer, row::Integer)`, a **multi-line** `<textarea>` will be shown, with the given dimensions.
  * If `size` is an integer, it controls the **width** of the single-line input.

# Examples

```julia
@bind author TextField()
```

```julia
@bind poem TextField((30,5); default="Hello\nJuliaCon!")
```
