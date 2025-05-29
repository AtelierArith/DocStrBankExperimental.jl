```
Atom(atom::Atom; kwargs...)
```

Update constructor. Construct a new `Atom`, by amending the data contained in the passed `atom` object. Supported `kwargs` include `species`, `mass`, as well as user-specific custom properties.

# Examples

Construct a standard hydrogen atom located at the origin

```julia-repl
julia> hydrogen = Atom(:H, zeros(3)u"Å")
```

and now amend its charge and atomic mass

```julia-repl
julia> Atom(atom; mass=1.0u"u", charge=-1.0u"e_au")
```
