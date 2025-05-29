```
Crystalline.KVec{D}(str::AbstractString) --> Crystalline.KVec{D}
Crystalline.KVec(str::AbstractString)    --> Crystalline.KVec
Crystalline.KVec(::AbstractVector, ::AbstractMatrix) --> Crystalline.KVec
Crystalline.KVec{D}(::AbstractVector, ::AbstractMatrix) --> Crystalline.KVec{D}
```

Return a `Crystalline.KVec` by parsing the string representations `str`, supplied in one of the following formats:

```jl
"($1,$2,$3)"
"[$1,$2,$3]"
"$1,$2,$3"
```

where the coordinates `$1`,`$2`, and `$3` are strings that may contain fractions, decimal numbers, and "free" parameters {`'α'`,`'β'`,`'γ'`} (or, alternatively and equivalently, {`'u'`,`'v'`,`'w'`} or {`'x'`,`'y'`,`'z'`}).

Fractions such as `1/2` and decimal numbers can be parsed: but use of any other special operator besides `/` will produce undefined behavior (e.g. do not use `*`).

## Example

```jldoctest
julia> Crystalline.KVec("0.25,α,0")
[1/4, α, 0]
```
