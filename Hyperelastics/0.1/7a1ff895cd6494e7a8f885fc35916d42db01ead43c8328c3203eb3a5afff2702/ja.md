```julia
YeohFleming()
YeohFleming(type)

```

# モデル:

$$
W = \frac{A}{B}(1-\exp{-B(I_1-3)}) - C_{10}(I_m-3)\log{1-\frac{I_1-3}{I_m-3}}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `A`
  * `B`
  * `C10`
  * `Im`

> Yeoh OH, Fleming PD. A new attempt to reconcile the statistical and phenomenological theories of rubber elasticity. Journal of Polymer Science Part B: Polymer Physics. 1997 Sep 15;35(12):1919-31.

