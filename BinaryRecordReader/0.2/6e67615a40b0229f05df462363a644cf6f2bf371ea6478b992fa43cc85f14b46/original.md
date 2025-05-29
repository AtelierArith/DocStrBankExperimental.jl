```
construct_reader_deep(S,array_specs)
```

Generates a `Base.read(io::IOStream, ::Type{S})` method that can used read type `S`, which is not an `isbitstype`.  If the class in question has other fields that made of up of other non-`isbitstype`s a full specification put in place  in the `array_spec`. The syntax for   `types` is `SubTypeName__fieldname`. 

# Example

```julia-repl
julia> struct C
            lat::Float32
            time::Matrix{Int32}
        end
julia> struct B
            fun::UInt8
            funMat::Matrix{UInt16}
        end
julia> struct A
            long::Float32
            COG::UInt16
            funky::AnotherSimpleRecMat
            data::Matrix{SimpleRecMat}
        end

julia> construct_reader_deep(A, (data=(5,5), B__funMat=(2,2), C__time =(3,3)))

```

The above will generate three `read` methods for all the three types defined. 

See also: `construct_reader_shallow`, `@construct_reader`
