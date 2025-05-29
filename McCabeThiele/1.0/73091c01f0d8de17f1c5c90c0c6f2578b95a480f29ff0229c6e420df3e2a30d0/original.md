`stages(data::Union{Matrix{Float64},Function}, z::Vector{Float64}; q::Number=NaN, R::Number=NaN, S::Number=NaN, updown::Bool=true, fig::Bool=true)`

`stages` computes the number of theoretical stages of a distillation column using the McCabe-Thiele method given a function y = y(x) that relates the liquid fraction x and the vapor fraction y or a x-y matrix of the liquid and the vapor fractions, the vector of products and feed compositions and two parameters among the feed quality, the reflux ratio at the top of the column and the reflux ratio at the bottom of the column.

By default, feed is a saturated liquid at the feed stage, q = 1.

If feed is a saturated liquid at the feed stage, q = 1, feed quality is reset to q = 1 - 1e-10.

By default, theoretical stages are computed from the stripping section to the rectifying section, updown = true.

If updown = false is given, theoretical stages are computed from the rectifying section to the stripping section.

By default, `stages` plots a schematic diagram of the solution, fig = true.

If fig = false is given, no plot is shown.

`stages` is a main function of the `McCabeThiele` toolbox for Julia.

See also: `refmin`, `qR2S`, `qS2R`, `RS2q`.

# Examples

Compute the number of theoretical stages of a distillation column from the bottom to the top of the column given a matrix that relates the liquid fraction and the vapor fraction, the composition of the distillate is 88 %, the composition of the feed is 46 %, the composition of the column's bottom product is 11 %, the feed is a liquid-vapor equilibrium with 44 % vapor at the feed stage and the reflux ratio at the top of the column is 70 % higher than the minimum reflux ratio:

```
data=[0.  0.;
      0.1 0.212;
      0.2 0.384;
      0.3 0.529;
      0.4 0.651;
      0.5 0.752;
      0.6 0.833;
      0.7 0.895;
      0.8 0.942;
      0.9 0.974;
      1.  1.];
x=[0.88;0.46;0.11];
r,s=refmin(data,x,q=1-0.44)
N=stages(data,x,q=1-0.44,R=1.70*r,updown=false,fig=false)
```

Compute the number of theoretical stages of a distillation column from the top to the bottom of the column given the function that compute the vapor fraction given the liquid fraction, the composition of the distillate is 88 %, the composition of the feed is 46 %, the composition of the column's bottom product is 11 %, the feed is saturated liquid at the feed stage and the reflux ratio at the top of the column is 70 % higher than the minimum reflux ratio and plot a schematic diagram of the solution:

```
y(x)=x.^0.9 .* (1-x).^1.2 + x;
x=[0.88;0.46;0.11];
r,s=refmin(y,x,q=1)
N=stages(y,x,q=1,R=1.70*r)
```
