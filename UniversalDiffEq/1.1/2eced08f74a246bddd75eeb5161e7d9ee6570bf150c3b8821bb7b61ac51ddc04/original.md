vectorfield*and*nullclines(UDE; kwargs)

Calculate the vector field and nullclines of the 2D `UDE` model and returns their plot.

# kwargs

-`t`: Time step `t` at which the vector field and nullclines are calculated. Default is `0`. -`n`: Number of elements per axes to evaluate vector field at. Default is `15`. -`lower`: Lower limits of vector field and nullclines. Default is `[0.0,0.0]`. -`upper`: Upper limits of vector field and nullclines. Default is `[1.0,1.0]`. -`arrowlength`: Arrow size of vector field plot. Default is `2`. -`arrow_color`: Arrow color of vector field plot. Default is `grey`. -`xlabel`: X-label of vector field plot. Default is `u1`. -`ylabel`: Y-label of vector field plot. Default is `u2`. -`title`: Plot title. Default is `Vector field`. -`color_u1`: Color of nullcline in x-axis. Default is `"red"`. -`color_u2`: Color of nullcline in y-axis. Default is `"black"`. -`legend`: Position of legends of nullcines in plot. Default is `:outerright`.
