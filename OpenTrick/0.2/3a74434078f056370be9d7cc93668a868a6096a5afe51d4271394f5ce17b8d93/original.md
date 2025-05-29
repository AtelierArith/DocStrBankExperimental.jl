```
opentrick(openfn[, args... [; <keyword arguments>]])
```

Call `openfn` with `(handlefn, args... ,kwargs ...)` as arguments, return an `IOWrapper` instance. (NB:`handlefn` is provided by `opentrick`.)

# Arguments

  * `openfn::Function` function actually called to obtain a `IO` instance. `openfn` must take a `Function(::IO)` instance as its first argument
  * `args` optional arguments that will be passed to `openfn`
  * `kwargs` optional keyword arguments that will be passed to `openfn`

# Examples

```jldoctest
julia> using OpenTrick

julia> filename = tempname();

julia> io = opentrick(open, filename, "w+");

julia> write(io, "hello world!")
12

julia> seek(io, 0);

julia> readline(io)
"hello world!"

```
