```
struct MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT}
```

Multi-Dimensional Bisection Methodのための主なデータを格納します。

# 例

```julia
include("MDBM.jl")
using Reexport
@reexport using .MDBM

function foo(x,y)
    x^2.0+y^2.0-2.0^2.0
end
function c(x,y) # c>0の領域のみを分析します
    x-y
end

ax1=Axis([-5,-2.5,0,2.5,5],"x") # x方向の初期グリッド
ax2=Axis(-5:2:5.0,"y") # y方向の初期グリッド

mymdbm=MDBM_Problem(foo,[ax1,ax2],constraint=c)
```
