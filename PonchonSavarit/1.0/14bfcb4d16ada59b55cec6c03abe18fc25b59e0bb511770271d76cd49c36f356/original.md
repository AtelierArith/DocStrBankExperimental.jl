`RS2q(data::Matrix{Float64}, z::Vector{Float64}, q::Number, R::Number)`

`RS2q` computes the feed quality of a distillation column using the Ponchon-Savarit method given a x-h-y-H matrix of the liquid and the vapor fractions at equilibrium and their enthalpies, the vector of the fractions of the products and the feed and the reflux ratios at the top and at the bottom of the column.

If feed is a saturated liquid, feed quality q = 1, feed quality is reset to q = 1 - 1e-10.

`RS2q` is a main function of the `PonchonSavarit` toolbox for Julia.

See also: `stages`, `refmin`, `qR2S`, `qS2R`.

# Examples

Compute the feed quality of a distillation column for acetone and methanol given a matrix that relates the liquid and the vapor fractions and their enthalpies at equilibrium, the composition of the distillate is 93 %, the composition of the feed is 41 %, the composition of the bottoms is 7 %, the reflux ratio at the top of the column is 2 and the reflux ratio at the bottom of the column is 1.7:

```
data=[2.5e-4 3.235 1.675e-3 20.720; # enthalpy in kcal/mol
      0.05   2.666 0.267    20.520;
      0.1    2.527 0.418    20.340;
      0.15   2.459 0.517    20.160;
      0.2    2.422 0.579    20.000;
      0.3    2.384 0.665    19.640;
      0.4    2.358 0.729    19.310;
      0.5    2.338 0.779    18.970;
      0.6    2.320 0.825    18.650;
      0.7    2.302 0.87     18.310;
      0.8    2.284 0.915    17.980;
      0.9    2.266 0.958    17.680;
      1.     2.250 1.       17.390];
x=[0.93;0.41;0.07];
q=RS2q(data,x,2.1,1.7)
```

Compute the feed quality of a distillation column for oxygen and nitrogen given a matrix that relates the liquid and the vapor fractions and their enthalpies at equilibrium, the composition of the distillate is 88 %, the composition of the feed is 44 %, the composition of the bottoms is 8 %, the reflux ratio at the top of the column is 2 and the reflux ratio at the bottom of the column is 1.3:

```
data=[0.    0.420 0.    1.840; # enthalpy in kcal/mmol
      0.075 0.418 0.193 1.755;
      0.17  0.415 0.359 1.685;
      0.275 0.410 0.50  1.625;
      0.39  0.398 0.63  1.570;
      0.525 0.378 0.75  1.515;
      0.685 0.349 0.86  1.465;
      0.88  0.300 0.955 1.425;
      1.    0.263 1.    1.405];
x=[0.88;0.44;0.08];
q=RS2q(data,x,2,1.3)
```
