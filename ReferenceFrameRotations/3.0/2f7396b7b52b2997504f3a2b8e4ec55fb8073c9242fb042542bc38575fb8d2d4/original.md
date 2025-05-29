```
Quaternion{T}
```

The definition of the quaternion.

# Fields

  * `q0::T`: Quaternion real part.
  * `q1::T`: X component of the quaternion imaginary part.
  * `q2::T`: Y component of the quaternion imaginary part.
  * `q3::T`: Z component of the quaternion imaginary part.

!!! note
    The quaternion `q` in this structure is represented by:

    ```
    q = q0 + q1.i + q2.j + q3.k
    ```


# Example

```julia-repl
julia> Quaternion(cosd(45), sind(45), 0, 0)
Quaternion{Float64}:
  + 0.7071067811865476 + 0.7071067811865476.i + 0.0.j + 0.0.k
```
