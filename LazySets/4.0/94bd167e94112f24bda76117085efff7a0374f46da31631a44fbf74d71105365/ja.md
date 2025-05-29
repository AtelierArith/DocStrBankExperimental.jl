```
project(P::AbstractPolyhedron, block::AbstractVector{Int}; [kwargs...])
```

多面体集合の具体的な射影。

### 入力

  * `P`     – 集合
  * `block` – ブロック構造、関心のある次元のベクトル

### 出力

`block`で指定された次元における`P`の射影を表す多面体。`P`が有界であった場合、結果は`HPolytope`となり、そうでない場合は`HPolyhedron`となることに注意してください。特定の入力タイプに対しては、異なる出力タイプを与えるより具体的なメソッドがあります。例えば、`Ball1`を射影すると`Ball1`が得られます。

### アルゴリズム

  * まず、`P`と`block`の各制約が*互換性*がある特別なケースを利用しようとします。これは以下の2つのケースの1つです。`c`を`P`の制約とし、$D_c$と$D_b$をそれぞれ`c`と`block`が制約されている次元の集合とします。

      * $$
        D_c ⊆ D_b
        $$

        の場合、`c`の法線ベクトルを射影できます。
      * $$
        D_c ∩ D_b = ∅
        $$

        の場合、制約は冗長になります。
  * 一般的な場合、与えられたブロック構造に関連する射影行列の具体的な線形写像を計算します。

### 例

4次元交差多面体（1ノルムにおける単位球）を考えます：

```jldoctest project_polyhedron
julia> P = convert(HPolytope, Ball1(zeros(4), 1.0));
```

すべての次元が制約されており、全空間への（自明な）射影を計算すると期待通りに動作します：

```jldoctest project_polyhedron
julia> constrained_dimensions(P)
4-element Vector{Int64}:
 1
 2
 3
 4

julia> project(P, [1, 2, 3, 4]) == P
true
```

交差多面体の各制約はすべての次元で制約されています。

次に、無限ノルムの球を取り、一部の制約を削除します：

```jldoctest project_polyhedron
julia> B = BallInf(zeros(4), 1.0);

julia> c = constraints_list(B)[1:2]
2-element Vector{HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}}:
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([1.0, 0.0, 0.0, 0.0], 1.0)
 HalfSpace{Float64, ReachabilityBase.Arrays.SingleEntryVector{Float64}}([0.0, 1.0, 0.0, 0.0], 1.0)

julia> P = HPolyhedron(c);

julia> constrained_dimensions(P)
2-element Vector{Int64}:
 1
 2
```

最後に、変数`1`と`2`への具体的な射影を行います：

```jldoctest project_polyhedron
julia> project(P, [1, 2]) |> constraints_list
2-element Vector{HalfSpace{Float64, Vector{Float64}}}:
 HalfSpace{Float64, Vector{Float64}}([1.0, 0.0], 1.0)
 HalfSpace{Float64, Vector{Float64}}([0.0, 1.0], 1.0)
```
