```
constrain(uv::AbstractUncertainScalarKDE,
    constraint::SamplingConstraint) -> TruncatedUncertainScalarKDE
```

Apply the `constraint` and truncate the support of an uncertain value `uv` represented by a kernel density estimate.
