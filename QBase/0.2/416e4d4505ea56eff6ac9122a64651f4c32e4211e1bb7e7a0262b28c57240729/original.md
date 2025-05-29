```
base_n_val(
    num_array :: Vector{Int64},
    base :: Int64;
    big_endian=true :: Bool
) :: Int64
```

Given an array representing a number in base-n returns the value of that number in base-10.

Inputs:

  * `num_array` - Vector containing semi-positive integers less than base.
  * `base` - The base-n number represented by num_array.
  * `big_endian` - `true` if most significant place is at index 1, else `false`.
