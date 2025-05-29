```
isotropic_elasticity_tensor(lambda::T, mu::T) where T <: Real
```

ラメパラメータ `lambda` と `mu` を持つ各向同性材料の弾性テンソル C(i,j,k,l)（ランク4、対称）を計算します。

(E, nu) がある場合は、`lame` を使用して (lambda, mu) を取得してください。
