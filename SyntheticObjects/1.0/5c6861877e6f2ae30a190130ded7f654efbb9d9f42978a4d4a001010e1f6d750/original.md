```
resolution_offset(sz = (100, 100, 1); numbers_or_alphabets="alphabets")

Create a 3D array of alphabets or numbers with varying font sizes and background levels.
```

# Arguments

  * `sz::Tuple`: A tuple of three integers representing the size of the volume. Default is (100, 100, 1).   Note that the first two elements are multiplied by 10 to defined the array size. The third elements will contain varying alphabets or numbers.
  * `numbers_or_alphabets::String`: A string representing whether to use alphabets or numbers. Default is "alphabets".

# Returns

```
A 3D array of alphabets or numbers with varying font sizes and background levels.
```

# Example

```jldoctest
julia> resolution_test(; sz_each_section=(100, 100), num_slices=1, numbers_or_alphabets="alphabets")
```
