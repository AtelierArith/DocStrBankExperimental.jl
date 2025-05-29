```
@mainname(file)
```

Return the main name of a file, i.e. the part before the last dot   and the extension.

# Examples

```julia
julia> @mainname("~/test.xyz")
("test", "xyz")
```
