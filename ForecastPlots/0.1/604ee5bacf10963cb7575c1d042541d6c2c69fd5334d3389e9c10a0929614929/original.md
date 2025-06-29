Package: ForecastPlots

```
fplot(x0, x1, px1, t=1:size(x0,1)+size(x1,1), args...; 
      plt = palette([:blue,:red],max(2,size(x0,2))), kw...)
```

Plot time series with its prediction intervals

# Arguments

  * `x0`: Vector or Matrix with time series
  * `x1`: Vector of Matrix forecast for x0
  * `px1`: Prediction intervals for x1 with size(px1) == (size(x1,1),2,N) where `N` is the number of intervals provided with the format [low*x1, high*x1].
  * `t`: Values for the temporal axis, it defaults to intengers starting at 1.
  * `args...`: `plot` arguments
  * `plt`: palette of colors for the time series, it defaults to palette([:blue,:red],max(2,size(x0,2)))
  * `kw...`: `plot` keyword arguments

# Returns

Forecast plots 

# Examples

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
