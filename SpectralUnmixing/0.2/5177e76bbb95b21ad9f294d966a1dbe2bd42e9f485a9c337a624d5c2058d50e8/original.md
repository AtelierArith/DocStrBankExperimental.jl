```
scale_data(refl::Matrix{Float64}, wavelengths::Vector{Float64}, criteria::String,
    bad_regions_wl=[[1300, 1500], [1800, 2000]])
```

Scale the reflectance data based on specified criteria.

# Arguments

  * `refl::Matrix{Float64}`: Reflectance data either size (n,) or (m,n), where n is the

number of bands and m the number of pixels.

  * `wavelengths::Vector{Float64}`: A vector of wavelengths of size (n,).
  * `criteria::String`: Normalization options:

      * `"none"`: No scaling will be applied, and the original reflectance data will be

    returned.

      * `"brightness"`: The data will be normalized based on brightness, excluding specified

    bad wavelength regions [1300, 1500] and [1800, 2000].

      * A specific wavelength (as a string): The data will be normalized using the reflectance

    value at this wavelength.
  * `bad_regions_wl`=[[1300, 1500], [1800, 2000]]: List of wavelength regions (in nm) to

ignore.

# Returns

  * A matrix of scaled reflectance data with same dimensions as `refl`.
