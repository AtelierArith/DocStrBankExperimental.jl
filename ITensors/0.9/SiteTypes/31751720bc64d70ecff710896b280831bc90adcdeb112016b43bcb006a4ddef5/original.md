```
siteinds(tag::String, N::Integer; kwargs...)
```

Create an array of `N` physical site indices of type `tag`. Keyword arguments can be used to specify quantum number conservation, see the `space` function corresponding to the site type `tag` for supported keyword arguments.

# Example

```julia
N = 10
s = siteinds("S=1/2", N; conserve_qns=true)
```
