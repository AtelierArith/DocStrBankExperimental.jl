```
qplot2(x::Array{Float64}, y::Array{Float64}, time::Array{Float64}, name::String, style::String, lineWidth=1, symSize=1):: Int32
```

plot with additional parameter (time?) info.

## Parameters:

```

'x', 'y': the line
'name' name of this line
'style'  the line style
'lineWidth' line width
'symSize' symbol size; 
'time' time info, for every point

```

## Example

```

julia-repl
julia> time=collect(0.0:0.01:10.0)
x = sin.(time)
y = cos.(time)
qfigure()
qplot(time, x + y, "function 1", "-b", 3)
qfigure()
qplot2(x, y, time, "function 2", "-m", 3)

```

Now use marker on both plots and see that it moves on both plots.

this function returns ID of the line created. hopefully you can use it in some other functions
ID supposed to be >=0 is all is OK, or <0 in case of error
