```
loglikelihood!(m, [needgrad=false], [needhess=false])
```

順序多項モデルの対数尤度を評価し、オプションで勾配とヘッセ行列を評価します。

# 位置引数

  * `m::PolrModel`: `PolrModel`型。対数尤度は、`m`のフィールド`Y`、`X`、`α`、`β`、および`link`に基づいて評価されます。
  * `needgrad::Bool=false`: 勾配を評価するかどうか。
  * `needhess::Bool=false`: フィッシャー情報行列（FIM）（負のヘッセ行列）を評価するかどうか。

# 出力

  * `logl`: 対数尤度。`needgrad=true`の場合、フィールド`m.∇`は`(θ, β)`に関する勾配（スコア）で上書きされます。`needhess=true`の場合、フィールド`m.FIM`は`(θ, β)`に関するフィッシャー情報行列（FIM）、すなわち負のヘッセ行列で上書きされます。
