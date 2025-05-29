```
CircleGroup
```

The circle group $𝕊^1$ is the unit circle together with composing points on the circle by adding angles. The circle itself is a one dimensional Riemannian manifold. Hence the Lie algebra is the real line.

The elements of the circle group can be represented in three different ways.

## As complex numbers

Elements of the circle group can be represented as complex numbers of absolute value one, that is

$$
𝕊¹ = \bigl\{ z ∈ ℂ\ \big|\ |z| = 1\bigr \} = \bigl\{ a + b\mathrm{i} ∈ ℂ\ \big|\ a^2+b^2 = 1\bigr \},
$$

where $\mathrm{i}$ denotes the imaginary unit. It is equipped with the group operation of complex multiplication [`AbelianMultiplicationGroupOperation`](@ref). That operation is given by

$$
(a + b\mathrm{i}) ∘ (c + d\mathrm{i}) := (ac - bd) + (ad + bc)\mathrm{i},
$$

for complex numbers $a + b\mathrm{i}, c + d\mathrm{i} ∈ ℂ$.

## As angles in $[-π,π)$

Elements of the circle group can be represented by the angle on the unit circle that they correspond to. In that case the elements are represented by real numbers $x ∈ [-π,π)$ and the circle group is identified with a quotient space of the real numbers

$$
 𝕊¹ = ℝ / 2πℤ = \bigl\{ [x] ∈ ℝ / 2πℤ\ \big|\ x ∈ [-π,π)\bigr \}.
$$

It is equipped with the group operation of adding angles $\mathrm{mod\, } 2π$ via [`AdditionGroupOperation`](@ref).

## As part of the 2D plane $ℝ^2$

Elements of the circle group can be represented as two dimensional real valued vectors $x ∈ ℝ$ of length 1. In that case the circle group is identified with the unit circle in $ℝ^2$, that is the one dimensional [`Sphere`](@extref `Manifolds.Sphere`)

$$
𝕊^1 = \bigl\{ (x, y) ∈ ℝ^2\ \big|\ x^2 + y^2 = 1\bigr \}.
$$

It is equipped with the group operation of adding the angles of two points on the unit circle which corresponds to complex multiplication

$$
(x_1, y_1) ∘ (x_2, y_2) := ( x_1x_2 - y_1y_2, x_1y_2 + x_2y_1),
$$

for real valued vectors $(x_1, y_1)^\mathrm{T}, (x_2, y_2)^\mathrm{T} ∈ ℝ^2$ via [`AbelianMultiplicationGroupOperation`](@ref).

# Constructors

```
CircleGroup(Circle(ℂ))
CircleGroup(ℂ)
CircleGroup()
```

Generate the circle group represented as complex numbers.

```
CircleGroup(Circle(ℝ))
CircleGroup(ℝ)
```

Generate the circle group represented as real valued angles $x ∈ [-π, π)$.

```
CircleGroup(Sphere(1))
CircleGroup(ℝ^2)
```

Generate the circle group represented as two dimensional real valued vectors of unit norm.

The default representation is by complex numbers and can be constructed with `CircleGroup()`.
