```
FastaReader(f::Function, filename::AbstractString, [sequence_type::Type = String])
```

This format of the constructor is useful for do-notation, i.e.:

```julia
FastaReader(filename) do fr
    # read out the data from fr, e.g.
    for (name, seq) in fr
        # do something with name and seq
    end
end
```

which ensures that the [`close`](@ref) function is called and is thus recommended (otherwise the file is closed by the garbage collector when the `FastaReader` object goes out of scope).
