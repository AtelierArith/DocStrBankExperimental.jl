```julia
InterpolatedModel(model, grid; algorithm)

```

Computes an representation of the model in the Fourier domain using interpolations and FFTs. This is useful to construct models that aren't directly representable in the Fourier domain.

# Note

This is mostly used for testing and debugging purposes. In general people should use the [`FourierDualDomain`](@ref) functionality to compute the Fourier transform of a model.
