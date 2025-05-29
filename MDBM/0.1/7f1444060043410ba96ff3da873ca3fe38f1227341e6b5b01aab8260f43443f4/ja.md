マルチディメンショナルバイセクション法（MDBM）は、高次元のサブマニフォールド（点、曲線、面…）の根を求めるために使用できる効率的で堅牢な根探索アルゴリズムです。これは、未知数の数が方程式の数を超える場合でも、暗黙の非線形方程式系の根を決定するために使用できます。

# 例

```julia
include("MDBM.jl")
using Reexport
@reexport using .MDBM

using PyPlot;
pygui(true);

function foo(x,y)
    x^2.0+y^2.0-2.0^2.0
end
function c(x,y) #c>0の領域のみを分析
    x-y
end

ax1=Axis([-5,-2.5,0,2.5,5],"x") # x方向の初期グリッド
ax2=Axis(-5:2:5.0,"y") # y方向の初期グリッド

mymdbm=MDBM_Problem(foo,[ax1,ax2],constraint=c)
iteration=5 #リファインメントの数（解像度の倍増）
solve!(mymdbm,iteration)


#関数fooが評価された点
x_eval,y_eval=getevaluatedpoints(mymdbm)

#解の補間点（おおよそfoo(x,y) == 0かつc(x,y)>0の場所）
x_sol,y_sol=getinterpolatedsolution(mymdbm)

fig = figure(1);clf()
scatter(x_eval,y_eval,s=5)
scatter(x_sol,y_sol,s=5)
```
