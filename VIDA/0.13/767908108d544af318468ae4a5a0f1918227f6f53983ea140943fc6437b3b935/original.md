```julia
divergence(d, m)

```

Computes the divergence of `d` with respect to the template `m`. This measure how similar the divergence with respect to the image stored in `d` is compared to the template.

# Arguments

  * `d`: An divergence or a subtype of [`VIDA.AbstractDivergence`](@ref)
  * `m`: A template which `ComradeBase.AbstractModel` or more commonly      a [`VIDA.AbstractImageTemplate`](@ref)
