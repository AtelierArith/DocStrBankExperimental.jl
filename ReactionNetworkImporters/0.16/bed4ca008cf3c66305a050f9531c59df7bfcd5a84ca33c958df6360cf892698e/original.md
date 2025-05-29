```
ParsedReactionNetwork(rn::ReactionSystem; u0 = nothing, p = nothing, varstonames = nothing, groupstosyms = nothing)
```

A container for storing a parsed reaction network along with its associated metadata.

# Fields

  * `rn`, a Catalyst `ReactionSystem`. **Note** this system is *not* marked complete by default (see the [Catalyst docs](https://catalyst.sciml.ai/) for a discussion of completeness of systems).
  * `u0`, a `Dict` mapping initial condition symbolic variables to numeric values and/or symbolic expressions.
  * `p`, a `Dict` mapping parameter symbolic variables to numeric values and/or symbolic expressions.
  * `varstonames`, a `Dict` mapping the internal symbolic variable of a species used in the generated `ReactionSystem` to a `String` generated from the name in the .net file. This is necessary as BioNetGen can generate exceptionally long species names, involving characters that lead to malformed species names when used with `Catalyst`.
  * `groupstosyms`, a `Dict` mapping the `String`s representing names for any groups defined in the BioNetGen file to the corresponding symbolic variable representing the `ModelingToolkit` symbolic observable associated with the group.
