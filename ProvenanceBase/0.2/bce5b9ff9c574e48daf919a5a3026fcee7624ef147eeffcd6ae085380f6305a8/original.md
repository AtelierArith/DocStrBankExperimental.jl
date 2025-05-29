```
provenance(object) -> NamedTuple
```

Describes the *provenance* of an `object` as a `NamedTuple`. Provenance here refers to the following:

> Provenance is information about entities, activities, and people involved in producing a piece of data or thing, which can be used to form assessments about its quality, reliability or trustworthiness.
>
> – https://www.w3.org/TR/prov-overview/


Returns `nothing` when no provenance has been captured from `object`.

Package authors with types that they wish to take part in provenance capture should extend `provenance` on their types. The definition *must* return a `NamedTuple` containing relevant provenance data associated with the `object`.

# Examples

```julia
struct MyType
    # ...
end

function ProvenanceBase.provenance(t::MyType)
    # Compute provenance data associated with `t`.
    return (
        # Assign provenance data to named fields and return it.
    )
end
```

# Data

`ProvenanceBase` does **not** prescribe a required set of provenance data that should be returned by these methods. It is up individual package authors to decide on the relevant data themselves.

Data that typically does not need to be captured is system-level data that is globally available, unless it is of direct relevance to the associated `object`. Data that would typically be included in the return value of `provenance` would be internal (or public) data of the `object` that needs a uniform access pattern.
