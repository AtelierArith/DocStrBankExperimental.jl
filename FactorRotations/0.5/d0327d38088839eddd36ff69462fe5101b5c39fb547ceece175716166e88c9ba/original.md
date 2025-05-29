```
PatternSimplicity(; orthogonal = false)
```

The *Pattern Simplicity* factor rotation criterion.

## Details

$$
Q_{\mathrm{PS}}(Λ) = \log \left\| \mathrm{diag}\left(\left(Λ²\right)ᵀ ⋅ Λ²\right) \right\| -
                      \log \left\| \left(Λ²\right)ᵀ ⋅ Λ² \right\|,
$$

where $Λ²$ is the matrix of squared loadings.

## Keyword arguments

  * `orthogonal`: If `orthogonal = true` an orthogonal rotation is performed, an oblique  rotation otherwise. (default: `false`)
