```
TransformedLogDensity(transformation, log_density_function)
```

ベイズ推論における問題。次元に互換性のある長さのベクトル（`transformation`から取得）を一般的なオブジェクト`θ`（制約のない型ですが、クリーンなコードのために名前付きタプルを推奨）に変換し、変換の対数ヤコビ行列式を補正します。

`log_density_function(θ)`は*実数*を返すことが期待されます。ゼロ密度や実現不可能な`θ`の場合、`-Inf`またはそれに類似した値が返されるべきですが、推論の効率のためにほとんどの手法はこれを避けるために`transformation`を使用することを推奨します。`log_density_function`は、問題のデータもカプセル化する呼び出し可能なオブジェクトであることが推奨されます。

プロパティアクセサ`ℓ.transformation`と`ℓ.log_density_function`を使用して、`ℓ::TransformedLogDensity`の引数にアクセスします。これらは公開APIの一部です。

# 使用上の注意

これは対数密度を定義する最も便利な方法であり、`capabilities`、`logdensity`、および`dimension`が自動的に定義されます。導関数をサポートする型を取得するには、[`ADgradient`](@ref)を使用してください。
