```
struct MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT}
```

Store the main data for the Multi-Dimensional Bisection Method.

# Examples

```julia
include("MDBM.jl")
using Reexport
@reexport using .MDBM

function foo(x,y)
    x^2.0+y^2.0-2.0^2.0
end
function c(x,y) #only the c>0 domain is analysed
    x-y
end

ax1=Axis([-5,-2.5,0,2.5,5],"x") # initial grid in x direction
ax2=Axis(-5:2:5.0,"y") # initial grid in y direction

mymdbm=MDBM_Problem(foo,[ax1,ax2],constraint=c)
```
