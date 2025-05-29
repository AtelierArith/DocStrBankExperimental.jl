```
CIB_Planck2013{T}(; kwargs...)
```

CIBモデルのパラメータを定義します。デフォルトはViero et al. 2013からのものです。タイプが指定されていないすべての数値はタイプTに変換されます。このモデルには以下のパラメータとデフォルト値があります：

  * `nside::Int64 = 4096`
  * `min_redshift = 0.0`
  * `max_redshift = 5.0`
  * `min_mass = 1e12`
  * `box_size = 40000`
  * `shang_zplat = 2.0`
  * `shang_Td = 20.7`
  * `shang_betan = 1.6`
  * `shang_eta = 2.4`
  * `shang_alpha = 0.2`
  * `shang_Mpeak = 10^12.3`
  * `shang_sigmaM = 0.3`
  * `shang_Msmin = 1e11`
  * `shang_Mmin = 1e10`
  * `shang_I0 = 92`
  * `jiang_gamma_1 = 0.13`
  * `jiang_alpha_1 = -0.83`
  * `jiang_gamma_2 = 1.33`
  * `jiang_alpha_2 = -0.02`
  * `jiang_beta_2 = 5.67`
  * `jiang_zeta = 1.19`
