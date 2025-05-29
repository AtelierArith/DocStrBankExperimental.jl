```
InverseLinearMap{N, S<:LazySet{N}, NM, MAT<:AbstractMatrix{NM}}
    <: AbstractAffineMap{N, S}

線形変換 $M$ が与えられたとき、この型はセット $X$ の線形変換 $M⁻¹⋅X$ を表しますが、実際に $M⁻¹$ を計算することはありません。

### フィールド

  * `M` – 行列（通常は可逆で、コンストラクタでチェックできます）
  * `X` – セット

### 注意事項

多くのセット操作は行列の逆を計算することを避けます。

原則として、多くのセット操作において行列は可逆である必要はありません（例えば、長方形であることも可能です）。

この型は逆線形写像の要素 `NM` に対してパラメトリックであり、ラップされたセットの数値型（`N`）とは独立しています。通常 `NM = N` ですが、例外があるかもしれません。例えば、`NM` が `N` 型の数値を保持する区間である場合、ここで `N` は `Float64` のような浮動小数点型です。

### 例

例のために $3×3$ 行列と単位三次元正方形を作成します。

```

jldoctest ilp_constructor julia> A = [1 2 3; 2 3 1; 3 1 2];

julia> X = BallInf([0, 0, 0], 1);

julia> ilm = InverseLinearMap(A, X) InverseLinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([1 2 3; 2 3 1; 3 1 2], BallInf{Int64, Vector{Int64}}([0, 0, 0], 1))

```

`InverseLinearMap` オブジェクトに逆線形写像を適用すると、2つの写像が単一の `InverseLinearMap` インスタンスに結合されます。

```

jldoctest ilp_constructor julia> B = transpose(A); ilm2 = InverseLinearMap(B, ilm) InverseLinearMap{Int64, BallInf{Int64, Vector{Int64}}, Int64, Matrix{Int64}}([14 11 11; 11 14 11; 11 11 14], BallInf{Int64, Vector{Int64}}([0, 0, 0], 1))

julia> ilm2.M == A*B true

```

`InverseLinearMap` を `ZeroSet` または `EmptySet` に適用すると、自動的に簡略化されます。

```

jldoctest ilp_constructor julia> InverseLinearMap(A, ZeroSet{Int}(3)) ZeroSet{Int64}(3) ```
