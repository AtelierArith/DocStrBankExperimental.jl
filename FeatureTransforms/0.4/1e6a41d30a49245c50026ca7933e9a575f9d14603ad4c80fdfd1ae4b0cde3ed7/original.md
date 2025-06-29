```
transform(::T, data)
```

Defines the feature engineering pipeline for some type `T`, which comprises a collection of [`Transform`](@ref)s and other steps to be peformed on the `data`.

The idea around a "transform interface” is to make feature transformations composable, i.e. the output of any one `Transform` should be valid input to another.

Feature engineering pipelines should obey the same principle and it should be trivial to add/remove `Transform` steps that compose the pipeline without it breaking.

`transform` should be overloaded for custom types `T` that require feature engineering. The only requirement is that the return of `transform`is itself "transformable", i.e. calling [`is_transformable`](@ref) on the output returns true.
