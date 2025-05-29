```
f2_norm(pf::T) where T<:Union{ProjectedF, FCoeffs}
```

$$
\int d^3 u \: f^2(u)
$$

の ProjectedF または FCoeffs に対しては、 $u_{\textrm{max}}^3 \sum_{n \ell m} f_{n \ell m}^2$ に等しいです。
