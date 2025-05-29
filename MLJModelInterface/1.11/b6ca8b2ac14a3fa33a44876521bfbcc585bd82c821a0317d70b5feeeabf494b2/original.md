```
metadata_pkg(T; args...)
```

Helper function to write the metadata for a package providing model `T`. Use it with broadcasting to define the metadata of the package providing a series of models.

## Keywords

  * `package_name="unknown"`   : package name
  * `package_uuid="unknown"`   : package uuid
  * `package_url="unknown"`    : package url
  * `is_pure_julia=missing`    : whether the package is pure julia
  * `package_license="unknown"`: package license
  * `is_wrapper=false` : whether the package is a wrapper

## Example

```julia
metadata_pkg.((KNNRegressor, KNNClassifier),
    package_name="NearestNeighbors",
    package_uuid="b8a86587-4115-5ab1-83bc-aa920d37bbce",
    package_url="https://github.com/KristofferC/NearestNeighbors.jl",
    is_pure_julia=true,
    package_license="MIT",
    is_wrapper=false)
```
