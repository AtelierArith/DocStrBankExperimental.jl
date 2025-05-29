```
CircleGroup
```

円群 $𝕊^1$ は単位円であり、円上の点を角度を加えることで合成します。円自体は一次元のリーマン多様体です。したがって、リー代数は実数直線です。

円群の要素は、三つの異なる方法で表現できます。

## 複素数として

円群の要素は、絶対値が1の複素数として表現できます。すなわち、

$$
𝕊¹ = \bigl\{ z ∈ ℂ\ \big|\ |z| = 1\bigr \} = \bigl\{ a + b\mathrm{i} ∈ ℂ\ \big|\ a^2+b^2 = 1\bigr \},
$$

ここで、$\mathrm{i}$ は虚数単位を示します。これは複素数の乗法の群演算 [`AbelianMultiplicationGroupOperation`](@ref) を備えています。その演算は次のように与えられます。

$$
(a + b\mathrm{i}) ∘ (c + d\mathrm{i}) := (ac - bd) + (ad + bc)\mathrm{i},
$$

複素数 $a + b\mathrm{i}, c + d\mathrm{i} ∈ ℂ$ に対して。

## $[-π,π)$ の角度として

円群の要素は、単位円上の対応する角度によって表現できます。この場合、要素は実数 $x ∈ [-π,π)$ で表され、円群は実数の商空間として同定されます。

$$
 𝕊¹ = ℝ / 2πℤ = \bigl\{ [x] ∈ ℝ / 2πℤ\ \big|\ x ∈ [-π,π)\bigr \}.
$$

これは角度を加える群演算 $\mathrm{mod\, } 2π$ を備えています [`AdditionGroupOperation`](@ref)。

## 2D平面 $ℝ^2$ の一部として

円群の要素は、長さ1の二次元実値ベクトル $x ∈ ℝ$ として表現できます。この場合、円群は $ℝ^2$ の単位円として同定されます。すなわち、一次元の [`Sphere`](@extref `Manifolds.Sphere`)

$$
𝕊^1 = \bigl\{ (x, y) ∈ ℝ^2\ \big|\ x^2 + y^2 = 1\bigr \}.
$$

これは、複素数の乗法に対応する単位円上の二点の角度を加える群演算を備えています。

$$
(x_1, y_1) ∘ (x_2, y_2) := ( x_1x_2 - y_1y_2, x_1y_2 + x_2y_1),
$$

実値ベクトル $(x_1, y_1)^\mathrm{T}, (x_2, y_2)^\mathrm{T} ∈ ℝ^2$ に対して、[`AbelianMultiplicationGroupOperation`](@ref) を介して。

# コンストラクタ

```
CircleGroup(Circle(ℂ))
CircleGroup(ℂ)
CircleGroup()
```

複素数として表現された円群を生成します。

```
CircleGroup(Circle(ℝ))
CircleGroup(ℝ)
```

実値の角度 $x ∈ [-π, π)$ として表現された円群を生成します。

```
CircleGroup(Sphere(1))
CircleGroup(ℝ^2)
```

単位ノルムの二次元実値ベクトルとして表現された円群を生成します。

デフォルトの表現は複素数によるもので、`CircleGroup()` で構築できます。
