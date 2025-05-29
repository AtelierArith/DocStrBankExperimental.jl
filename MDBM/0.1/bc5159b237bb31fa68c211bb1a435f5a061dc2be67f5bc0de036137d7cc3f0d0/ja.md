```
struct MDBM_Problem{fcT,N,Nf,Nc,t01T,t11T,IT,FT}
```

マルチ次元二分法のための主要なデータを格納します。

# 例

```julia
include("MDBM.jl")
using Reexport
@reexport using .MDBM

function foo(x,y)
    x^2.0+y^2.0-2.0^2.0
end
function c(x,y) # c>0 の領域のみを分析します
    x-y
end

ax1=Axis([-5,-2.5,0,2.5,5],"x") # x方向の初期グリッド
ax2=Axis(-5:2:5.0,"y") # y方向の初期グリッド

mymdbm=MDBM_Problem(foo,[ax1,ax2],constraint=c)
```
