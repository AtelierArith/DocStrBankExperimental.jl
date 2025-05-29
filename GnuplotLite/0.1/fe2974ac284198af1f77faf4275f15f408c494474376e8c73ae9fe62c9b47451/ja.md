```
 send(::Pair{String,@NamedTuple{x::T,y::T,z::U}}) where
    {T <: AbstractVector{<:Real}, U <: AbstractMatrix{<:Real}}
```

行列をGnuplotに送信し、変数に格納します。このバリアントは、非一様行列に関するGnuplotのドキュメントに記載されているように、行列とともに軸情報も送信します。

[`Msg`](@ref)を返します。

例:

```
    x = y = -1:0.1:1
    z = x.^2 .- y'.^2
    gnuplot() do gp
        gp |> 
            send("data" => (x=collect(x), y=collect(y), z=z)) |>
            send("splot $data w l")
    end
```
