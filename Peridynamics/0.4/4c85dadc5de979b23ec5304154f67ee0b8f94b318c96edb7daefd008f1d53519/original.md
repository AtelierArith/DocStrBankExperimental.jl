```
point_set!(body, set_name, points)
point_set!(fun, body, set_name)
```

Add a point set to a [`Body`](@ref). The points of the set can be either specified directly with the `points::AbstractVector` argument, or as the result of the filter function `fun`. By default, a body already contains a point set with the name `:all_points`, containg a set with all points.

# Arguments

  * `body::AbstractBody`: [`Body`](@ref) where the set will be added.
  * `set_name::Symbol`: Name of the point set.
  * `points::AbstractVector`: Some vector containing the point indices of the set.   The indices have to be in bounds with the `position` and `volume` of `body`.
  * `fun::Function`: Function for filtering points. This function accepts only one positional   argument and will be used in a `findall` call. Depending on the argument name,   a different input will be processed:

      * `x`: The function will receive the x-coordinate of each point in `position` of `body`:

        ```julia
        points = findall(fun, @view(position[1, :]))
        ```
      * `y`: The function will receive the y-coordinate of each point in `position` of `body`:

        ```julia
        points = findall(fun, @view(position[2, :]))
        ```
      * `z`: The function will receive the z-coordinate of each point in `position` of `body`:

        ```julia
        points = findall(fun, @view(position[3, :]))
        ```
      * `p`: The function will receive the a vector containing each dimension of each point in `position` of `body`:

        ```julia
        points = findall(fun, eachcol(position))
        ```

# Throws

  * Error if a point set with the same `set_name` already exists.
  * Error if `points` are not in bounds with `position` and `volume` of the `body`.

# Examples

Add a point set to `body` with all points that have a x-corrdinate larger than zero:

```julia-repl
julia> point_set!(x -> x > 0, body, :larger_than_zero)

julia> point_sets(body)
Dict{Symbol, Vector{Int64}} with 2 entries:
  :larger_than_zero => [6, 7, 8, 9, 10, 16, 17, 18, 19, 20  …  9…
  :all_points       => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  991, 9…
```

Add a point set to `body` with all points that are positioned inside a sphere with radius `r` around the center. Note that the `do`-syntax can be used, as `fun` is the first argument of `point_set!`:

```julia-repl
julia> point_set!(body, :inside_sphere) do p
           sqrt(p[1]^2 + p[2]^2 + p[3]^2) ≤ r
       end

julia> point_sets(body)
Dict{Symbol, Vector{Int64}} with 2 entries:
  :larger_than_zero => [6, 7, 8, 9, 10, 16, 17, 18, 19, 20  …  9…
  :inside_sphere    => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  991, 9…
```
