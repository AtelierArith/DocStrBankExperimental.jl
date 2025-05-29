```
writecsv2(f, A; opts...)
```

Equivalent to `writedlm2()` with fixed delimiter `','` and `decimal='.'`.

# Code Example

```jldoctest
julia> using ReadWriteDlm2

julia> B = Any[1 complex(1.5,2.7);1.0 1//3];

julia> writecsv2("test.csv", B)

julia> read("test.csv", String)
"1,1.5+2.7im\n1.0,1//3\n"
```
