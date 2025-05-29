```
ionstate(ion::Ion, sublevel)
```

Retuns the ket corresponding to the `Ion` being in state $|sublevel⟩$. Options: sublevel <: Tuple{String,Real}: Specifies full sublevel name sublevel <: String: Specifies sublevel alias sublevel <: Int: Returns the `sublevel`th eigenstate
