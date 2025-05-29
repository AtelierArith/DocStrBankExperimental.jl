```
amoeba(f; alg=Polygonal(), options...)
```

関数 `f` のアメーバを、与えられたアルゴリズム `alg` を使用して計算します。`alg` には以下のものが含まれます。

  * `Polygonal()`
  * `Greedy()`
  * `ArchTrop()`
  * `Simple()`

ただし、通常は `Polygonal()` または `Greedy()` を使用することをお勧めします。

与えられたアルゴリズムに応じて、関数は異なるキーワード引数を取ります。

## 例

```julia
@polyvar x y

# これは `Polygonal()` アルゴリズムを使用します
amoeba(x^2 + y^2 + 1)

# 大まかな近似を求めるだけです
amoeba(x^2 + y^2 + 1, accuracy=0.1)

# `Greedy()` アルゴリズムを使用します。
amoeba(x^2 + y^2 + 1, alg=Greedy())

# カスタムグリッドを使用して `Greedy()` アルゴリズムを使用します。
grid = Grid2D(xlims=(-5, 5), ylims=(-4, 4), res=(500, 400))
amoeba(x^2 + y^2 + 1, alg=Greedy(), grid=grid)

# デフォルトのドメインを使用しますが、解像度を高くします
amoeba(x^2 + y^2 + 1, alg=Greedy(), resolution=800)
```

## `Polygonal()`

このアルゴリズムは、提供された `domain` Ω におけるアメーバ $\mathcal{A}(f)$ の近似を計算します。これは、|𝒫| ⊂ Ω となる多角形の集合 𝒫 を計算し、これらの多角形の合併が外側から $\mathcal{A}(f)$ ∩ Ω を近似するようにします。

可能な（オプションの）引数は以下の通りです。

  * `domain`: アメーバ $\mathcal{A}(f)$ が計算されるセクション Ω を定義する `(xmin, xmax, ymin, ymax)` 形式のタプル。このドメインは、Ω ∩ $\mathcal{A}(f)$ が $\mathcal{A}(f)$ の正しいトポロジーを捉えるものでなければなりません。
  * `accuracy=0.01`: 最大許容誤差 |𝒫 - $\mathcal{A}(f)$ ∩ Ω|。誤差の上限のみを計算することに注意してください。

与えられた精度に達するとアルゴリズムは停止します。

  * `spine`: このアルゴリズムは $\mathcal{A}(f)$ のスパインを必要とします。
  * `minimal_component_size=0.01`: 補集合のコンポーネントの最小サイズ。これは、スパインが明示的に渡されていない場合にのみ使用されます。
  * `iterations=2000`: 最大反復回数。
  * `vertices_accuracy=accuracy*1e-3`: アルゴリズム中に、$\mathcal{A}(f)$ の境界上の点を近似します。これは、それらを計算する精度です。この値は近似の最小誤差に影響を与え、常に `accuracy` よりもいくつかの桁小さいものであるべきです。
  * `membership_options=[MembershipTestOptions()](@ref)`: サブルーチンとしてメンバーシップテストが使用されます。

## `Greedy()`, `Simple()`, `ArchTrop()`

これらのアルゴリズムはすべて、グリッドに基づくアメーバ $\mathcal{A}(f)$ の近似です。これは基本的に異なるグリッドポイントに対してメンバーシップテストを適用します。`Greedy()` が最も速く、`Simple()` が最も遅いです。グリッドは明示的に渡すことができ、そうでなければヒューリスティックに基づいて計算されます。

  * `resolution=600`: 明示的に渡されない場合のグリッドの解像度。
  * `grid`: 明示的に渡された場合、このグリッドが使用されます。そうでなければヒューリスティックに基づいて計算されます。
  * `membership_options=[MembershipTestOptions()](@ref)`: メンバーシップテストのオプション。

```
