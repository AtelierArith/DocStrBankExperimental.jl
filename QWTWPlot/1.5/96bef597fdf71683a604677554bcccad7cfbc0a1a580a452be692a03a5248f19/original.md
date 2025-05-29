qplot1(x::Vector{Float64}, y::Vector{Float64}, name::String, style::String, symSize):: Int32

plot lines with line width == 1.

```

x and y:   the points   
name:      	name for this line   
style: 	 	how to draw a line   
symSize:	size of the symbols  

```

what does 'style' parameter means? It's a string which has 1 or 2 or 3 symbols. 
Look at two places for the detail explanation:

  * example code  https://github.com/ig-or/QWTWPlot.jl/blob/master/src/qwexample.jl
  * https://github.com/ig-or/QWTWPlot.jl/blob/master/docs/line-styles.md

this function returns ID of the line created. hopefully you can use it in some other functions
ID supposed to be >=0 is all is OK, or <0 in case of error
