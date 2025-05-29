パッケージ: ForecastPlots

```
fplot(x0, x1, px1, t=1:size(x0,1)+size(x1,1), args...; 
      plt = palette([:blue,:red],max(2,size(x0,2))), kw...)
```

予測区間を持つ時系列をプロットする

# 引数

  * `x0`: 時系列のベクトルまたは行列
  * `x1`: x0の予測のベクトルまたは行列
  * `px1`: x1の予測区間で、size(px1) == (size(x1,1),2,N) であり、ここで `N` は [low*x1, high*x1] 形式で提供される区間の数です。
  * `t`: 時間軸の値で、デフォルトは1から始まる整数です。
  * `args...`: `plot` 引数
  * `plt`: 時系列の色のパレットで、デフォルトは palette([:blue,:red],max(2,size(x0,2))) です。
  * `kw...`: `plot` キーワード引数

# 戻り値

予測プロット 

# 例

```julia-repl
x0 = rand(20);
x1 = rand(10);
px1 = zeros(10,2,2);
px1[:,1,1] .= -0.2; px1[:,2,1] .= 0.2;
px1[:,1,2] .= -0.4; px1[:,2,2] .= 0.4;

fplot(x0,x1,px1)

xb0 = rand(20) .+ 2;
xb1 = rand(10) .+ 2;
px1 = zeros(10,2,2,2)
px1[:,1,1,1] .= -0.2; px1[:,2,1,1] .= 0.2;
px1[:,1,2,1] .= -0.4; px1[:,2,2,1] .= 0.4;
px1[:,1,1,2] .= -0.2; px1[:,2,1,2] .= 0.2;
px1[:,1,2,2] .= -0.4; px1[:,2,2,2] .= 0.4;

xx0 = [x0 xb0]
xx1 = [x1 xb1]
fplot(xx0, xx1, px1)

using Dates
fplot(x0,x1,px1,now()-Day(20+10-1):Day(1):now())
```
