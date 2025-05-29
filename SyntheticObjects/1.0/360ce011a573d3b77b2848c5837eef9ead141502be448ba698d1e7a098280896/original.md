```
annotation_3D!(sz=(128,128, 1); numbers_or_alphabets="alphabets", font_size=Float64.(minimum(sz[1:2]))-10.0, bkg=0.9)

Create a 3D array of alphabets or numbers with varying font sizes and background levels.
```

# Arguments

  * `sz::Tuple`: A tuple of three integers representing the size of the volume. Default is (128, 128, 1).
  * `numbers_or_alphabets::String`: A string representing whether to use alphabets or numbers. Default is "alphabets".
  * `font_size::Float64`: A float representing the font size. Default is the minimum of the first two elements of `sz` minus 10.0.
  * `bkg::Float64`: A float representing the background level. Default is 0.9.

# Returns

```
A 3D array of alphabets or numbers with varying font sizes and background levels.
```
