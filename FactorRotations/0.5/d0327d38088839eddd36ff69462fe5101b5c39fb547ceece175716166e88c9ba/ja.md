```
PatternSimplicity(; orthogonal = false)
```

*パターンの単純性*因子回転基準。

## 詳細

$$
Q_{\mathrm{PS}}(Λ) = \log \left\| \mathrm{diag}\left(\left(Λ²\right)ᵀ ⋅ Λ²\right) \right\| -
                      \log \left\| \left(Λ²\right)ᵀ ⋅ Λ² \right\|,
$$

ここで、$Λ²$は二乗負荷の行列です。

## キーワード引数

  * `orthogonal`: `orthogonal = true`の場合は直交回転が行われ、それ以外の場合は斜交回転が行われます。（デフォルト: `false`）
