```julia
triunsuitable!(unsuitable::Function; check_signature)

```

Set triunsuitable callback used by Triangle if the '-u' flag is set.

This is a function called by Triangle with the coordinates of the vertices of a triangle in order to learn if that triangle needs further  refinement (i.e. 'true' returned) or not ('false' returned).

Other checks (e.g. maximum edge lengths) are possible here as well.

Note, that the handling of this function is currently not thread safe.

```
function unsuitable(x1,y1,x2,y2,x3,y3,area)
    myarea=locally_desired_area(x1,y1,x2,y2,x3,y3)
    if area>myarea 
       return true
    else 
       return false
    end
end
```
