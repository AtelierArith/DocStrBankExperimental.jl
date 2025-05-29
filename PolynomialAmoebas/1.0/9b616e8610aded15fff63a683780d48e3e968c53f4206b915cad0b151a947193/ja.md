```
spine(f::MP.AbstractPolynomial; options...)
```

アモーバ $\mathcal{A}(f)$ のスパインを計算します。このアルゴリズムはまず $\mathcal{A}(f)$ の近似を計算し、そこからスパインを求めます。Spine2D を返します。

## 例

```julia
@polyvar x y
# すべてのデフォルトを使用
spine(x^2 + y^2 + 1)

# アモーバの補集合に非常に小さな成分があると考えられる場合
# 明示的なドメインを使用したい
spine(x^2 + y^2 + 1, domain=(-5, 5, -5, 5), minimal_component_size=0.001)
```

オプション引数:

  * `minimal_component_size=0.01`: $\mathcal{A}(f)$ の補集合の各成分にこの直径のボールが収まることを保証します。

これが成り立たない場合、アルゴリズムは誤った結果を返す可能性があります。

  * `domain`: アモーバ $\mathcal{A}(f)$ が計算されるセクション Ω を定義する形式 `(xmin, xmax, ymin, ymax)` のタプルです。このドメインは、Ω ∩ $\mathcal{A}(f)$ が $\mathcal{A}(f)$ の正しいトポロジーを捉えるようにする必要があります。
  * `grid`: `minimal_component_size` と `domain` に基づいて、グリッドを自動的に計算できます。

このオプションで上書きすることも可能です。

  * `membership_options=[MembershipTestOptions](@ref)()`: メンバーシップテストのオプション。
  * `nsamples=1024`: 計算のために数値的に積分を評価します。これは計算に使用されるサンプルポイントの数です。

```
spine(f::MP.AbstractPolynomial, A::Bitmap2D; nsamples=1024)
```

与えられたアモーバ近似 `A` に基づいてスパインを計算します。
