```
isotropic_compliance_tensor(lambda::T, mu::T) where T <: Real
```

各成分 S(i,j,k,l) (ランク4、対称) を計算します。これは、ラメパラメータ `lambda` と `mu` を持つ等方性材料のためのものです。

(E, nu) を持っている場合は、`lame` を使用して (lambda, mu) を取得してください。
