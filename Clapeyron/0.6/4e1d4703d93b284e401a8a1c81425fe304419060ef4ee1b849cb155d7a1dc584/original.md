```
MultiFluid(components;
    idealmodel = nothing,
    ideal_userlocations = String[],
    pure_userlocations = String[],
    mixing = AsymmetricMixing,
    departure = EmpiricDeparture,
    mixing_userlocations = String[],
    departure_userlocations = String[],
    estimate_pure = false,
    estimate_mixing = :off,
    coolprop_userlocations = true,
    Rgas = nothing,
    reference_state = nothing,
     verbose = false)
```

## Input parameters

  * JSON data (CoolProp and teqp format)

## Input models

  * `idealmodel`: Ideal Model. if it is `nothing`, then it will parse the ideal model from the input JSON.
  * `mixing`: mixing model for temperature and volume.
  * `departure`: departure model

## Description

Instantiates a multi-component Empiric EoS model. `Rgas` can be used to set the value of the gas constant that is used during property calculations.

If `coolprop_userlocations` is true, then Clapeyron will try to look if the fluid is present in the CoolProp library.

If `estimate_pure` is true, then, if a JSON is not found, the pure model will be estimated, using the `XiangDeiters` model

`estimate_mixing` is used to fill missing mixing values in the case of using `AsymmetricMixing`. on other mixing models it has no effect.

  * `estimate_mixing = :off` will perform no calculation of mixing parameter, throwing an error if missing values are found.
  * `estimate_mixing = :lb` will perform Lorentz-Berthelot estimation of missing mixing parameters. (γT = βT = γv = βv = 1.0). additionally, you can pass `LorentzBerthelotMixing` to use `k` and `l` BIP instead.
  * `estimate_mixing = :linear` will perform averaging of γT and γv so that `T(x) = ∑xᵢTᵢ` and `V(x) = ∑xᵢVᵢ` on missing mixing parameters. Additionally, you can use `LinearMixing` to perform this directly.

`Rgas` sets the value of the gas constant to be used by the multifluid. The default is the following:

  * If `Rgas` is not specified and the input is a single component model, then the value of `Rgas` will be taken from the fluid json file.
  * If `Rgas` is not specified and the input is a multi-component model, then the value of `Rgas` will be set to `Clapeyron.R̄ = Rgas() = 8.31446261815324` (2019 defined constant value)
