```
SWSFun{TR<:AbstractFloat}()
(swsf::SWSFun{TR})(θ::TR)
coefficients(swsf::SWSFun)
```

球面加重球面調和関数。固有ベクトルは次の方程式の $C$ 係数を含みます：

$$
{}_s S_{\ell m}(x; c)=\sum_{\ell^{\prime}=\ell_{\min }}^{\infty} C_{\ell^{\prime} \ell m}(c) {}_s S_{\ell^{\prime} m}(x; 0)
$$

ここで、$C$ は次のように正規化されます：

$$
\sum_{\ell^{\prime}=\ell_{\text {min }}}^{\ell_{\max }}\left|C_{\ell^{\prime} \ell m}(c)\right|^2=1
$$

そして位相は $C_{\ell^{\prime} \ell m}(c)$ が $\ell^{\prime}=\ell$ のとき実数となるように選ばれます [Cook:2014cta](@cite)。スピン加重球面調和関数は次のように正規化されます：

$$
\int_0^\pi {}_s S_{\ell m}(x; c) {}_s S^*_{\ell m}(x; c) \sin(\theta) d\theta = 1
$$

# 引数

  * `s::Integer`: スピン
  * `c::Complex{TR}`: 扁平度パラメータ
  * `m::Integer`: 方位数
  * `l::Integer`: 角数
  * `l_max::Integer`: 最大角数
