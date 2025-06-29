`refmin(data::Union{Matrix{Float64},Function}, z::Vector{Float64}; q::Number=1)`

`refmin` computes the minimum reflux ratios at the top and the bottom of a distillation column using the McCabe-Thiele method given a function y = y(x) that relates the liquid fraction x and the vapor fraction y, or a x-y matrix of the liquid and the vapor fractions, the vector of the fractions of the distillate and the feed and the feed quality.

By default, feed is a saturated liquid at the feed stage, q = 1.

If feed is a saturated liquid at the feed stage, q = 1, feed quality is reset to q = 1 - 1e-10.

`refmin` is a main function of the `McCabeThiele` toolbox for Julia.

See also: `stages`, `qR2S`, `qS2R`, `RS2q`.

# Examples

Compute the minimum value of the reflux ratio of a distillation column given a matrix that relates the liquid fraction and the vapor fraction, the composition of the distillate is 88 %, the composition of the feed is 46 %, the composition of the column's bottom product is 11 % and the feed is a liquid-vapor equilibrium with 44 % vapor at the feed stage:

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
```

Compute the minimum value of the reflux ratio of a distillation column given the function that compute the vapor fraction given the liquid fraction, the composition of the distillate is 88 %, the composition of the feed is 46 %, the composition of the column's bottom product is 11 % and the feed is saturated liquid at the feed stage:

```
y(x)=x.^0.9 .* (1-x).^1.2 + x;
x=[0.88;0.46;0.11];
r,s=refmin(y,x,q=1)
```
