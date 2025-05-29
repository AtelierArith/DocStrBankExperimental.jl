```julia
fit(formula::FormulaTerm, data::DataFrame, modelClass::LinearRegression, bootstrap::Boot_Residual, sim_size::Int64 = 1000)
```

Fit a Bootstrap Regression model on the input data. Uses the [lm](https://juliastats.org/GLM.jl/stable/api/#GLM.lm) method from the [GLM](https://github.com/JuliaStats/GLM.jl) package under the hood. Returns an object of type `DataFrame`.

# Example

```julia-repl
julia> using CRRao, RDatasets, StableRNGs, StatsModels
julia> df = dataset("datasets", "mtcars")
32×12 DataFrame
 Row │ Model              MPG      Cyl    Disp     HP     DRat     WT       QSec     VS     AM     Gear   Carb  
     │ String31           Float64  Int64  Float64  Int64  Float64  Float64  Float64  Int64  Int64  Int64  Int64 
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ Mazda RX4             21.0      6    160.0    110     3.9     2.62     16.46      0      1      4      4
   2 │ Mazda RX4 Wag         21.0      6    160.0    110     3.9     2.875    17.02      0      1      4      4
   3 │ Datsun 710            22.8      4    108.0     93     3.85    2.32     18.61      1      1      4      1
   4 │ Hornet 4 Drive        21.4      6    258.0    110     3.08    3.215    19.44      1      0      3      1
   5 │ Hornet Sportabout     18.7      8    360.0    175     3.15    3.44     17.02      0      0      3      2
   6 │ Valiant               18.1      6    225.0    105     2.76    3.46     20.22      1      0      3      1
  ⋮  │         ⋮             ⋮       ⋮       ⋮       ⋮       ⋮        ⋮        ⋮       ⋮      ⋮      ⋮      ⋮
  27 │ Porsche 914-2         26.0      4    120.3     91     4.43    2.14     16.7       0      1      5      2
  28 │ Lotus Europa          30.4      4     95.1    113     3.77    1.513    16.9       1      1      5      2
  29 │ Ford Pantera L        15.8      8    351.0    264     4.22    3.17     14.5       0      1      5      4
  30 │ Ferrari Dino          19.7      6    145.0    175     3.62    2.77     15.5       0      1      5      6
  31 │ Maserati Bora         15.0      8    301.0    335     3.54    3.57     14.6       0      1      5      8
  32 │ Volvo 142E            21.4      4    121.0    109     4.11    2.78     18.6       1      1      4      2
                                                                                                 20 rows omitted
julia> CRRao.set_rng(StableRNG(123))
StableRNGs.LehmerRNG(state=0x000000000000000000000000000000f7)
julia> container = fit(@formula(MPG ~ HP + WT + Gear), df, LinearRegression(), Boot_Residual())
4×5 DataFrame
 Row │ Predictor    Coef        Std Error   Lower 5%    Upper 95%  
     │ String       Float64     Float64     Float64     Float64    
─────┼─────────────────────────────────────────────────────────────
   1 │ (Intercept)  32.1309     4.57528     24.8024     39.9568
   2 │ HP           -0.0364971  0.00962225  -0.0519917  -0.0201571
   3 │ WT           -3.22576    0.834607    -4.61517    -1.80358
   4 │ Gear          1.00012    0.842335    -0.429382    2.35324
```
