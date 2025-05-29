```
CodeGenContext(;
    vars=Variables(:p, :p_end, :is_eof, :cs, :data, :mem, :byte, :buffer),
    generator=:table,
    getbyte=Base.getindex,
    clean=false
)
```

Create a `CodeGenContext` (ctx), a struct that stores options for Automa code generation. Ctxs are used for Automa's various code generator functions. They currently take the following options (more may be added in future versions)

  * `vars::Variables`: variable names used in generated code. See the `Variables` struct.
  * `generator::Symbol`: code generator mechanism (`:table` or `:goto`). The table generator creates smaller, simpler code that uses a vector of integers to determine state transitions. The goto-generator uses a maze of `@goto`-statements, and create larger, more complex code, that is faster.
  * `getbyte::Function` (table generator only): function `f(data, p)` to access byte from data. Default: `Base.getindex`.
  * `clean`: Whether to remove some `QuoteNode`s (line information) from the generated code

# Example

```julia
julia> ctx = CodeGenContext(generator=:goto, vars=Variables(buffer=:tbuffer));

julia> generate_code(ctx, compile(re"a+")) isa Expr
true
```
