```
ll, e = correct!(pf, u, y, p = parameters(f), t = index(f))
```

測定 `y` に基づいて状態/重みを更新し、対数尤度と予測誤差を返します（粒子フィルタの場合、誤差は常に0です）。

# 拡張ヘルプ

異なるセンサーに対して別々の測定更新を行うには、[ドキュメントの「測定モデル」](@ref measurement_models)を参照してください。[`AdvancedParticleFilter`](@ref)の場合、カスタム `measurement_likelihood` 関数をキーワード引数 `g` として `correct!` に渡すか、カスタム `measurement_likelihood` を使用して低レベル関数 `measurement_equation!` を呼び出すことで実現できます。
