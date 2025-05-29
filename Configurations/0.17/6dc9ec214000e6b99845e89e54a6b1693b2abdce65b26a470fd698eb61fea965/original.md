```
@option [alias::String] <struct def>
```

Define an option struct type. This will auto-generate methods that parse a given `Dict{String}` object (the keys must be of type `String`) into an instance of the struct type you defined. One can use `alias` string to distinguish multiple possible option type for the same field.

# Special Types

  * `Maybe{T}`: this type is equivalent to `Union{Nothing, T}` and   is treated specially in `@option`, it will always have a default   value of `nothing` if not specified.
  * [`Reflect`](@ref): this type is treated specially to allow one to use a field   to store the corresponding type information.

!!! compat "Configurations 0.16"
    from v0.16.0 Configurations stops overloading the `Base.show` method for you, if you need pretty printing of your option types, consider overloading the `Base.show(io::IO, mime::MIME, x)` method to `pprint_struct(io, mime, x)` provided by [GarishPrint](https://github.com/Roger-luo/GarishPrint.jl)


!!! compat "Configurations 0.12"
    from v0.12.0 the field alias feature is removed due to the syntax conflict with field docstring. Please refer to [#17](https://github.com/Roger-luo/Configurations.jl/issues/17).


# Example

One can define option type via `@option` macro with or without an alias.

```julia-repl
julia> "Option A"
       @option "option_a" struct OptionA
           name::String
           int::Int = 1
       end

julia> "Option B"
       @option "option_b" struct OptionB
           opt::OptionA = OptionA(;name = "Sam")
           float::Float64 = 0.3
       end
julia> option = from_dict(OptionB, d)
OptionB(;
    opt = OptionA(;
        name = "Roger",
        int = 2,
    ),
    float = 0.33,
)
```

when there are multiple possible option type for one field, one can use the alias to distinguish them

```julia-repl
julia> @option struct OptionD
           opt::Union{OptionA, OptionB}
       end

julia> d1 = Dict{String, Any}(
               "opt" => Dict{String, Any}(
                   "option_b" => d
               )
           );

julia> from_dict(OptionD, d1)
OptionD(;
    opt = OptionB(;
        opt = OptionA(;
            name = "Roger",
            int = 2,
        ),
        float = 0.33,
    ),
)
```
