```
@construct_reader S array_specs
```

Generates a `Base.read(io::IOStream, ::Type{S})` method that can used read type `S`, which is not an `isbitstype`. 

# Example

```julia-repl
julia> struct CompoundStruct
           long::Float32
           COG::UInt16
           data::Matrix{Float64}
       end
julia> @construct_reader CompoundStruct (data=(10,10),)
```

The above will generate a suitable `read` method assuming that the `data` field is a 10x10 matrix. 

See also: `construct_reader_deep`, `@construct_reader`
