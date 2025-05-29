```
struct EvaluatedMeasure <: BATMeasure
```

Combined a measure with samples, and other information on it.

Constructors:

```julia
EvaluatedMeasure(
    measure;
    samples = ..., approx = ..., mass = ..., mode = ...,
    _generator = ...
)
```

!!! note
    Field `_generator` does not form part of the stable public API and is subject to change without deprecation.

