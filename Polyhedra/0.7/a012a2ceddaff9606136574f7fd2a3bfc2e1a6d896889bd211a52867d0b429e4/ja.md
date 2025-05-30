```
hrep(hyperplanes::HyperPlaneIt, halfspaces::HalfSpaceIt; d::FullDim)
```

次元 `d` の全次元の多面体の H-表現を作成します。これは、ハイパープレーン `hyperplanes` とハーフスペース `halfspaces` の交差によって得られます。

### 例

例えば、単体は次のように表現できます。

$$
\begin{aligned}
  x_1 + x_2 &= 1 \\
  x_1 &\geq 0 \\
  x_2 &\geq 0
\end{aligned}
$$

次のように作成できます。

```jldoctest
julia> hrep([HyperPlane([1, 1], 1)], [HalfSpace([0, -1], 0), HalfSpace([-1, 0], 0)])
H-representation Polyhedra.Intersection{Int64, Vector{Int64}, Int64}:
1-element iterator of HyperPlane{Int64, Vector{Int64}}:
 HyperPlane([1, 1], 1),
2-element iterator of HalfSpace{Int64, Vector{Int64}}:
 HalfSpace([0, -1], 0)
 HalfSpace([-1, 0], 0)
```
