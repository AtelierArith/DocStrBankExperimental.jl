```
 send(::Pair{String,@NamedTuple{x::T,y::T,z::U}}) where
    {T <: AbstractVector{<:Real}, U <: AbstractMatrix{<:Real}}
```

Send a matrix to Gnuplot, storing it in a variable. This variant also sends axis information along with the matrix, as described in the Gnuplot documentation for nonuniform matrices.

Returns a [`Msg`](@ref).

Example:

```
    x = y = -1:0.1:1
    z = x.^2 .- y'.^2
    gnuplot() do gp
        gp |> 
            send("data" => (x=collect(x), y=collect(y), z=z)) |>
            send("splot $data w l")
    end
```
