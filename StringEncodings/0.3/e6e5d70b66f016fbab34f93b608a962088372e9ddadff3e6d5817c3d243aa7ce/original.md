```
read(stream::IO, [nb::Integer,] enc::Encoding)
read(filename::AbstractString, [nb::Integer,] enc::Encoding)
read(stream::IO, ::Type{String}, enc::Encoding)
read(filename::AbstractString, ::Type{String}, enc::Encoding)
```

Methods to read text in character encoding `enc`. See documentation for corresponding methods without the `enc` argument for details.
