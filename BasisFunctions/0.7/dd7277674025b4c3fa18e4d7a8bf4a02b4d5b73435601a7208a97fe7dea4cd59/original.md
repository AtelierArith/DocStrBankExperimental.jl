A `ParamDict` is a dictionary combined with a map, which is the parameterization of some domain that is the image of the support of the dictionary.

If `Ω` is a domain, parameterized by the function `κ : P → Ω`, then the `ParamDict` is a dictionary defined on `P`, with each point `t ∈ P` identified with `x = κ(t) ∈ Ω`. The `ParamDict` acts like any other dictionary on `P`.

Note the difference with a `MappedDict`, which is defined on `Ω`. Operations on mapped dictionaries require an easily invertible map.
