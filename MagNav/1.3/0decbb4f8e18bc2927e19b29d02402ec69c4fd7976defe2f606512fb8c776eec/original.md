```
LinCompParams <: CompParams
```

Linear aeromagnetic compensation parameters struct. Subtype of `CompParams`.

To see default parameters, type `LinCompParams()`.

**General Parameters:**

| **Parameter**      | **Type**         | **Description**                                                                                                                                                                                |
|:------------------ |:---------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `version`          | VersionNumber    | MagNav.jl version used to generate this struct                                                                                                                                                 |
| `features_setup`   | Vector{`Symbol`} | vector of features to include, only used for `model_type = :elasticnet, :plsr`                                                                                                                 |
| `features_no_norm` | Vector{`Symbol`} | vector of features to not normalize, only used for `model_type = :elasticnet, :plsr`                                                                                                           |
| `model_type`       | Symbol           | aeromagnetic compensation model type (`see below`)                                                                                                                                             |
| `y_type`           | Symbol           | `y` target type (`see below`)                                                                                                                                                                  |
| `use_mag`          | Symbol           | uncompensated scalar magnetometer to use for `y` target vector {`:mag_1_uc`, etc.}, only used for `y_type = :c, :d, :e`                                                                        |
| `use_vec`          | Symbol           | vector magnetometer (fluxgate) to use for "external" Tolles-Lawson `A` matrix {`:flux_a`, etc.}, only used for `model_type = :TL, :mod_TL, :map_TL`                                            |
| `data_norms`       | Tuple            | length-`4` tuple of data normalizations, `(A_bias,A_scale,y_bias,y_scale)` for `model_type = :TL, :mod_TL, :map_TL` or `(x_bias,x_scale,y_bias,y_scale)` for `model_type = :elasticnet, :plsr` |
| `model`            | Tuple            | linear model coefficients                                                                                                                                                                      |
| `terms`            | Vector{`Symbol`} | Tolles-Lawson terms to use for Tolles-Lawson `A` matrix (or matrices) within `x` data matrix {`:permanent`,`:induced`,`:eddy`}, only used for `model_type = :elasticnet, :plsr`                |
| `terms_A`          | Vector{`Symbol`} | Tolles-Lawson terms to use for "external" Tolles-Lawson `A` matrix {`:permanent`,`:induced`,`:eddy`,`:bias`}, only used for `model_type = :TL, :mod_TL, :map_TL`                               |
| `sub_diurnal`      | Bool             | if true, subtract diurnal from scalar magnetometer measurements                                                                                                                                |
| `sub_igrf`         | Bool             | if true, subtract IGRF from scalar magnetometer measurements                                                                                                                                   |
| `bpf_mag`          | Bool             | if true, bpf scalar magnetometer measurements in `x` data matrix, only used for `model_type = :elasticnet, :plsr`                                                                              |
| `reorient_vec`     | Bool             | if true, align vector magnetometers (fluxgates) with body frame                                                                                                                                |
| `norm_type_A`      | Symbol           | normalization for "external" Tolles-Lawson `A` matrix, only used for `model_type = :TL, :mod_TL, :map_TL` (`see below`)                                                                        |
| `norm_type_x`      | Symbol           | normalization for `x` data matrix, only used for `model_type = :elasticnet, :plsr` (`see below`)                                                                                               |
| `norm_type_y`      | Symbol           | normalization for `y` target vector (`see below`)                                                                                                                                              |

  * `model_type` options:

      * `:TL`         = classical Tolles-Lawson
      * `:mod_TL`     = modified  Tolles-Lawson
      * `:map_TL`     = map-based Tolles-Lawson
      * `:elasticnet` = elastic net (ridge regression and/or Lasso)
      * `:plsr`:      = partial least squares regression (PLSR)
  * `y_type` options:

      * `:a` = anomaly field  #1, compensated tail stinger total field scalar magnetometer measurements
      * `:b` = anomaly field  #2, interpolated `magnetic anomaly map` values
      * `:c` = aircraft field #1, difference between uncompensated cabin total field scalar magnetometer measurements and interpolated `magnetic anomaly map` values
      * `:d` = aircraft field #2, difference between uncompensated cabin and compensated tail stinger total field scalar magnetometer measurements
      * `:e` = BPF'd total field, bandpass filtered uncompensated cabin total field scalar magnetometer measurements
  * `norm_type` options:

      * `:standardize` = Z-score normalization
      * `:normalize`   = min-max normalization
      * `:scale`       = scale by maximum absolute value, bias = 0
      * `:none`        = scale by 1, bias = 0

**Linear Model-Specific Parameters:**

| **Parameter** | **Type** | **Description**                                                     |
|:------------- |:-------- |:------------------------------------------------------------------- |
| `k_plsr`      | Int64    | number of components, only used for `model_type = :plsr`            |
| `λ_TL`        | Float64  | ridge parameter, only used for `model_type = :TL, :mod_TL, :map_TL` |
