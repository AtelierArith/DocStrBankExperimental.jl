```
ResetMap{N, S<:LazySet{N}} <: AbstractAffineMap{N, S}
```

遅延リセットマップを表す型です。リセットマップは、線形マップ $A$ がすべてのリセット次元でゼロエントリを持つ単位行列であるアフィンマップ $A x + b, x ∈ X$ の特別なケースであり、翻訳ベクトル $b$ は他のすべての次元でゼロです。

### フィールド

  * `X`      – 集合
  * `resets` – リセット（インデックスから新しい値へのマッピング）

### 注意事項

リセットマップは凸性を保持します：もし `X` が凸であれば、`X` の任意のリセットマップも凸です。

### 例

```jldoctest resetmap
julia> X = BallInf([2.0, 2.0, 2.0], 1.0);

julia> r = Dict(1 => 4.0, 3 => 0.0);

julia> rm = ResetMap(X, r);

```

ここで `rm` は集合 `X` を修正し、`x1` を 4 にリセットし、`x3` を 0 にリセットしますが、`x2` は変更されません。したがって、`rm` は集合 `VPolytope([[4.0, 1.0, 0.0], [4.0, 3.0, 0.0]])` に相当し、すなわち 3D に埋め込まれた軸に沿った線分です。

対応するアフィンマップ $A x + b$ は次のようになります：

$$
    egin{pmatrix} 0 & 0 & 0 \ 0 & 1 & 0 \ 0 & 0 & 0 nd{pmatrix} x +
    egin{pmatrix} 4 & 0 & 0 nd{pmatrix}
$$

関数 `matrix`（または `vector`）を使用して、与えられたリセットマップに対応する行列 `A`（またはベクトル `b`）を作成します。

```jldoctest resetmap
julia> matrix(rm)
3×3 LinearAlgebra.Diagonal{Float64, Vector{Float64}}:
 0.0   ⋅    ⋅
  ⋅   1.0   ⋅
  ⋅    ⋅   0.0

julia> vector(rm)
3-element SparseArrays.SparseVector{Float64, Int64} with 1 stored entry:
  [1]  =  4.0
```

`ResetMap` を `ZeroSet` または `EmptySet` に適用すると、自動的に簡略化されます。

```jldoctest resetmap
julia> ResetMap(ZeroSet(3), r)
Singleton{Float64, SparseArrays.SparseVector{Float64, Int64}}(sparsevec([1], [4.0], 3))

julia> ResetMap(EmptySet(3), r)
∅(3)
```

`rm` の方向 `[1, 1, 1]` における（この場合は一意の）サポートベクトルは次の通りです：

```jldoctest resetmap
julia> σ(ones(3), rm)
3-element Vector{Float64}:
 4.0
 3.0
 0.0
```
