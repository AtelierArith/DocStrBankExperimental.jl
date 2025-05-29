```
NNCompParams <: CompParams
```

Neural network-based aeromagnetic compensation parameters struct. Subtype of `CompParams`.

To see default parameters, type `NNCompParams()`.

**General Parameters:**

| **Parameter**      | **Type**         | **Description**                                                                                                                               |
|:------------------ |:---------------- |:--------------------------------------------------------------------------------------------------------------------------------------------- |
| `version`          | VersionNumber    | MagNav.jl version used to generate this struct                                                                                                |
| `features_setup`   | Vector{`Symbol`} | vector of features to include                                                                                                                 |
| `features_no_norm` | Vector{`Symbol`} | vector of features to not normalize                                                                                                           |
| `model_type`       | Symbol           | aeromagnetic compensation model type (`see below`)                                                                                            |
| `y_type`           | Symbol           | `y` target type (`see below`)                                                                                                                 |
| `use_mag`          | Symbol           | uncompensated scalar magnetometer to use for `y` target vector {`:mag_1_uc`, etc.}, only used for `y_type = :c, :d, :e`                       |
| `use_vec`          | Symbol           | vector magnetometer (fluxgate) to use for "external" Tolles-Lawson `A` matrix {`:flux_a`, etc.}, not used for `model_type = :m1`              |
| `data_norms`       | Tuple            | length-`7` tuple of data normalizations, `(A_bias,A_scale,v_scale,x_bias,x_scale,y_bias,y_scale)`                                             |
| `model`            | Chain            | neural network model                                                                                                                          |
| `terms`            | Vector{`Symbol`} | Tolles-Lawson terms to use for Tolles-Lawson `A` matrix (or matrices) within `x` data matrix {`:permanent`,`:induced`,`:eddy`}                |
| `terms_A`          | Vector{`Symbol`} | Tolles-Lawson terms to use for "external" Tolles-Lawson `A` matrix {`:permanent`,`:induced`,`:eddy`,`:bias`}, not used for `model_type = :m1` |
| `sub_diurnal`      | Bool             | if true, subtract diurnal from scalar magnetometer measurements                                                                               |
| `sub_igrf`         | Bool             | if true, subtract IGRF from scalar magnetometer measurements                                                                                  |
| `bpf_mag`          | Bool             | if true, bpf scalar magnetometer measurements in `x` data matrix                                                                              |
| `reorient_vec`     | Bool             | if true, align vector magnetometers (fluxgates) with body frame                                                                               |
| `norm_type_A`      | Symbol           | normalization for "external" Tolles-Lawson `A` matrix, only used for `model_type = :m2*` (`see below`)                                        |
| `norm_type_x`      | Symbol           | normalization for `x` data matrix (`see below`)                                                                                               |
| `norm_type_y`      | Symbol           | normalization for `y` target vector (`see below`)                                                                                             |

  * `model_type` options are broken into 3 architectures, with `1` being a standard feedforward neural network and `2` & `3` being used in conjunction with Tolles-Lawson

      * `:m1`   = standard feedforward neural network (NN)
      * `:m2a`  = NN determines Tolles-Lawson (TL) coefficients
      * `:m2b`  = NN determines additive correction to classical TL
      * `:m2c`  = NN determines additive correction to classical TL, TL coefficients tuned as well
      * `:m2d`  = NN determines additive correction to each TL coefficient
      * `:m3tl` = no NN, TL coefficients fine-tuned via SGD, without Taylor expansion for `y_type = :b, :c` (for testing)
      * `:m3s`  = NN determines scalar correction to TL, using expanded TL vector terms for explainability
      * `:m3v`  = NN determines vector correction to TL, using expanded TL vector terms for explainability
      * `:m3sc` = `:m3s` with curriculum learning based on TL error
      * `:m3vc` = `:m3v` with curriculum learning based on TL error
      * `:m3w`  = `:m3s` with window NN for temporal dataset
      * `:m3tf` = `:m3s` with time series transformer for temporal dataset
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

**Neural Network-Based Model-Specific Parameters:**

| **Parameter**  | **Type**          | **Description**                                                                                      |
|:-------------- |:----------------- |:---------------------------------------------------------------------------------------------------- |
| `TL_coef`      | Vector{`Float64`} | Tolles-Lawson coefficients, not used for `model_type = :m1, :m2a`                                    |
| `η_adam`       | Float64           | learning rate for Adam optimizer                                                                     |
| `epoch_adam`   | Int64             | number of epochs for Adam optimizer                                                                  |
| `epoch_lbfgs`  | Int64             | number of epochs for LBFGS optimizer                                                                 |
| `hidden`       | Vector{`Int64`}   | hidden layers & nodes (e.g., `[8,8]` for 2 hidden layers, 8 nodes each)                              |
| `activation`   | Function          | activation function (`see below`)                                                                    |
| `loss`         | Function          | loss function (`see below`)                                                                          |
| `batchsize`    | Int64             | mini-batch size                                                                                      |
| `frac_train`   | Float64           | fraction of training data used for training (remainder for validation), only used for Adam optimizer |
| `α_sgl`        | Float64           | Lasso (`α_sgl=0`) vs group Lasso (`α_sgl=1`) balancing parameter {0:1}                               |
| `λ_sgl`        | Float64           | sparse group Lasso parameter, typically ~1e-5 (if non-zero)                                          |
| `k_pca`        | Int64             | number of components for pre-processing with PCA + whitening, `-1` to ignore                         |
| `drop_fi`      | Bool              | if true, perform drop-column feature importance                                                      |
| `drop_fi_bson` | String            | path/name of drop-column feature importance data BSON file to save/load (`.bson` extension optional) |
| `drop_fi_csv`  | String            | path/name of drop-column feature importance data CSV file to save (`.csv` extension optional)        |
| `perm_fi`      | Bool              | if true, perform permutation feature importance                                                      |
| `perm_fi_csv`  | String            | path/name of permutation feature importance data CSV file to save (`.csv` extension optional)        |

  * `activation` options, which can be visualized by running `plot_activation()`:

      * `relu`  = rectified linear unit
      * `σ`     = sigmoid (logistic function)
      * `swish` = self-gated
      * `tanh`  = hyperbolic tan
  * `loss` options:

      * `mse`        = mean squared error
      * `mae`        = mean absolute error
      * `huber_loss` = mean Huber loss
