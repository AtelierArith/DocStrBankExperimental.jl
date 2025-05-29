```
UnivariateARCHModel(spec::UnivariateVolatilitySpec, data::Vector; dist=StdNormal(),
          			meanspec=NoIntercept(), fitted=false
          			)
```

UnivariateARCHModelを作成します。

# 例:

```jldoctest
julia> UnivariateARCHModel(GARCH{1, 1}([1., .9, .05]), randn(10))

GARCH{1, 1} モデル（ガウス誤差）、T=10.


─────────────────────────────────────────
                             ω   β₁    α₁
─────────────────────────────────────────
ボラティリティパラメータ:     1.0  0.9  0.05
─────────────────────────────────────────
```
