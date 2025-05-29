```
LRG_Yuan23{T}(; kwargs...)
```

Define LRG model parameters. Defaults from Yuan et al. 2023 [arXiv:2306.06314]. All numbers not typed are converted to type T. This model has the following parameters and default values:

  * `nside::Int64 = 4096`
  * `hod::String = "zheng"`
  * `min_redshift = 0.0`
  * `max_redshift = 5.0`
  * `min_mass = 1e12`
  * `box_size = 40000`
  * `shang_Msmin = 1e11`
  * `zheng_Mcut = 10^12.7`
  * `zheng_M1 = 10^13.6`
  * `zheng_sigma = 0.2`
  * `zheng_kappa = 0.08`
  * `zheng_alpha = 1.15`
  * `yuan_ic = 0.8`
  * `jiang_gamma_1 = 0.13`
  * `jiang_alpha_1 = -0.83`
  * `jiang_gamma_2 = 1.33`
  * `jiang_alpha_2 = -0.02`
  * `jiang_beta_2 = 5.67`
  * `jiang_zeta = 1.19`
