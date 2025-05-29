```
generate_perimeter_point(norm_distance_on_perimeter::Float64, e::Ellipse)
```

`e` に含まれるパラメータで定義された楕円の周囲において、距離 `norm_distance_on_perimeter` $\times$ `e.circumference` の位置にある単一の点を生成します。点は長さ2のベクトルとして返されます。

# 引数

  * `norm_distance_on_perimeter`: 楕円の周囲における正規化された距離を表す数値 ∈ [0.0,1.0]。値 `0.5` は楕円の周囲の中間点に対応し、値 `0.7` は楕円の周囲の70%の位置に対応します。
  * `e`: 楕円を定義する有効な [`EllipseSampling.Ellipse`](@ref) 構造体。

# 詳細

点は、回転前の主軸上の最も正の頂点から始めて、楕円の周囲を反時計回りにサンプリングされます。回転が適用された後、この頂点は主軸上の最も正の頂点でなくなる場合があります。ここでの頂点とは、主軸上にあり楕円と交差する2つの端点を意味します。

平行移動や回転成分がない楕円を考えます。x半径が `2.0` で y半径が `1.0` の場合、x軸が主軸になります。その結果、`norm_distance_on_perimeter=0.0` の値は点 `[x,y] = [2.0, 0.0]` に対応します。`norm_distance_on_perimeter=0.25` の値は、楕円の周囲を $\frac{π}{2}$ 反時計回りに回転した位置に対応し、点 `[x,y] = [0.0, 1.0]` に対応します。

```julia
using EllipseSampling
e = construct_ellipse(2.0, 1.0)
generate_perimeter_point(0.0, e)
generate_perimeter_point(0.25, e)
```

同様に、x半径が `1.0` で y半径が `2.0` の場合、y軸が主軸になります。その結果、`norm_distance_on_perimeter=0.0` の値は点 `[x,y] = [0.0, 2.0]` に対応します。`norm_distance_on_perimeter=0.25` の値は、楕円の周囲を $\frac{π}{2}$ 反時計回りに回転した位置に対応し、点 `[x,y] = [-1.0, 0.0]` に対応します。

```julia
e = construct_ellipse(1.0, 2.0)
generate_perimeter_point(0.0, e)
generate_perimeter_point(0.25, e)
```

楕円が円である場合（主軸と副軸が同じ半径を持つ）、点は回転前のx半径の最も正の点から始めて、楕円の周囲を反時計回りにサンプリングされます。

楕円が回転したときのサンプリングの動作を示すために、簡単のため半径1.0の円で、平行移動成分がなく、反時計回りに $\frac{π}{2}$ 回転した楕円を考えます。この場合、x軸は90度反時計回りに回転しているため、`norm_distance_on_perimeter=0.0` の値は点 `[x,y] = [0.0, 1.0]` に対応します。`norm_distance_on_perimeter=0.25` の値は、回転した楕円の周囲を $\frac{π}{2}$ 反時計回りに回転した位置に対応し、点 `[x,y] = [-1.0, 0.0]` に対応します。

```julia
e = construct_ellipse(1.0, 1.0, pi/2)
generate_perimeter_point(0.0, e)
generate_perimeter_point(0.25, e)
```

## ランダムサンプリング

この関数は、最初に [0,1] で定義された一様分布から N 点をサンプリングし、その後各点 1:N に対してこの関数を呼び出すことで、楕円から一様なランダムサンプルを生成するのに簡単に使用できます。

例えば、次のように使用します：

```julia
using EllipseSampling
e = construct_ellipse(2.0,1.0)
N = 100
samples = rand(N)
points = generate_perimeter_point.(samples, Ref(e))
```

ここでは、Julia が `e` に対してもブロードキャストしないように、楕円構造体 `e` を `Ref` でラップしています。この方法で生成された点を、[`generate_N_equally_spaced_points`](@ref) によって生成された点と同じ列方向の形式で取得するには、次のようにします：

```julia
points = reduce(hcat, points)
```

[0,1] で定義された他の分布を使用して、同様の方法で楕円の周囲の点を生成することもできます。 ```
