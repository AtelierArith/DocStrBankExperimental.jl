```
ActionNoise(
    action, # グループアクション G ⊂ Diff(M)
    covariance, # 関数 M -> AbstractPDMat
    basis # Alg(G) の固定基底
)
```

リー代数上で定義された共分散。対応する分布は、関数 ξ ↦ \exp(ξ)⋅x₀ によってリー代数上の正規分布をプッシュフォワードしたもので、x₀ を中心としています。
