```
TangentDiffBackend <: AbstractRiemannianDiffBackend
```

接線空間とその基底を使用して、内因的な微分スキームを導出するバックエンドです。

引数と関数値の接線空間で動作するため、メソッドはリトラクションと逆リトラクション、さらに基底を必要とする場合があります。

接線空間自体では、このバックエンドは（ユークリッド）バックエンドを使用します。

# コンストラクタ

```
TangentDiffBackend(diff_backend)
```

ここで `diff_backend` は接線空間で使用される（ユークリッド）バックエンドです。

キーワード引数として

  * `retraction` は [AbstractRetractionMethod](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/retractions.html) （デフォルトは `ExponentialRetraction`）
  * `inverse_retraction` は [AbstractInverseRetractionMethod](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/retractions.html) （デフォルトは `LogarithmicInverseRetraction`）
  * `basis_arg` は [AbstractBasis](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/bases.html) （デフォルトは `DefaultOrthogonalBasis`）
  * `basis_val` は [AbstractBasis](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/bases.html) （デフォルトは `DefaultOrthogonalBasis`）
