```
RecombinedBSplineBasis{k, T}
```

特定の同次境界条件（BC）を満たすために、[`BSplineBasis`](@ref)の再結合から定義された機能基底です。

# 拡張ヘルプ

基底再結合技術は、Galerkin法におけるBCの適用の一般的な方法です。これは、Boyd 2000（第6章）で、チェビシェフ基底の文脈で説明されています。このアプローチでは、元の基底 $\{b_i(x), 1 ≤ i ≤ N\}$ が新しい基底 $\{ϕ_j(x), 1 ≤ j ≤ M\}$ に「再結合」され、各基底関数 $ϕ_j$ が選択されたBCを個別に満たすようにします。

再結合された基底の長さ $M$ は、元の基底の長さ $N$ よりも常に小さくなります。差 $δ = N - M$ は、境界条件の数に等しいです。最も単純（かつ一般的）な場合では、各境界に対して単一のBCが適用され、$δ = 2$ になります。より一般的には、以下でさらに説明するように、異なるBCを同時に課すことが可能であり、これにより自由度の数がさらに減少します（$δ$ が増加します）。

Bスプラインの局所サポートのおかげで、基底再結合は元のBスプライン基底のごく一部のみを含みます。たとえば、各境界で非ゼロのBスプラインは1つだけであるため、その関数を基底から削除するだけで同次Dirichlet BCを適用するのに十分です。導関数に対するBCを課すことはやや複雑ですが、依然として可能です。

基底再結合と[コレクション法](@ref collocation-api)を組み合わせる場合、境界にコレクションポイントが**ない**必要があります。そうしないと、結果として得られるコレクション行列が逆行列を持たない可能性があります。

## 境界条件の次数

このセクションでは、基底が満たすべき単一の同次境界条件 $\mathrm{d}^n u / \mathrm{d}x^n = 0$ の最も単純なケースを考えます。

再結合された基底は、2つの境界で適用される同次BCの次数を決定する `Derivative` オブジェクトの指定を必要とします。`Derivative` の線形結合もサポートされています。Bスプラインの次数は $k ≥ n + 1$ である必要があります。なぜなら、次数 $k$ のBスプラインは $C^{k - 1}$-連続関数だからです（ノットでは $C^{k - 1 - p}$ であり、$p$ はノットの重複度です）。

一般的な選択肢は次のとおりです：

  * `Derivative(0)` は同次[Dirichlet BC](https://en.wikipedia.org/wiki/Dirichlet_boundary_condition)（境界での $u = 0$）を設定し、最初と最後のBスプラインを削除します。すなわち、$ϕ_1 = b_2$;
  * `Derivative(1)` は同次[Neumann BC](https://en.wikipedia.org/wiki/Neumann_boundary_condition)（境界での $u' = 0$）を設定し、最初の2つ（および最後の2つ）のBスプラインを追加します。すなわち、$ϕ_1 = b_1 + b_2$。
  * より一般的には、`α Derivative(0) + β Derivative(1)` は同次[Robin BC](https://en.wikipedia.org/wiki/Robin_boundary_condition)を設定し、$ϕ_1$ を $b_1$ と $b_2$ の線形結合として定義します。ここで重要なのは、`Derivative(1)` が境界での[法線導関数](https://en.wikipedia.org/wiki/Directional_derivative#Normal_derivative) $\frac{∂u}{∂n}$ を示し、これは左境界で $-\frac{∂u}{∂x}$ に等しいことです。

高次のBCも可能です。たとえば、`Derivative(2)` は最初の3つのBスプラインを再結合して、左境界で $ϕ_1'' = ϕ_2'' = 0$ を満たす2つの基底関数を生成しますが、低次および高次の導関数が境界で自由度を保持することを保証します。最初の3つのBスプラインを単に追加する（$ϕ_1 = b_1 + b_2 + b_3$）と、最初の導関数と2番目の導関数が消えてしまうため、望ましくありません。

`Derivative(2)` の場合、選択された解は $ϕ_i = α_i b_i + β_i b_{i + 1}$ と設定されます（$i ∈ \{1, 2\}$）。$α_i$ と $β_i$ の係数は、境界で $ϕ_i'' = 0$ となるように選ばれます。さらに、整合性のために、各 $i$ に対して $α_i + β_i = 2$ という（やや恣意的な）制約を満たします。これは高次のBCにも一般化されます。各境界関数 $ϕ_i$ が隣接する2つのBスプラインからのみ定義されるため、その局所サポートは最小限に保たれ、結果として得られる行列の小さなバンド幅を保持します。

最後に、現在の実装では、両方の境界に異なる境界条件を課すことはできないことに注意してください。

## 複数の境界条件

オプションとして、再結合された基底は異なる次数の同次BCを同時に満たすことができます。この場合、`Derivative` のタプルを渡す必要があります。

サポートされているBCの組み合わせの詳細については、以下で文書化されている異なる `RecombinedBSplineBasis` コンストラクタを参照してください。

---

```
RecombinedBSplineBasis(B::BSplineBasis, op::AbstractDifferentialOp)
RecombinedBSplineBasis(B::BSplineBasis, op_left, op_right)
```

Bスプライン基底 `B` から `RecombinedBSplineBasis` を構築し、与えられた微分演算子に関連する同次境界条件（BC）を満たします。

2番目のケースでは、各境界に異なるBCを設定できます。

たとえば、`op = Derivative(0)` と `op = Derivative(1)` は、それぞれ同次DirichletおよびNeumann BCに対応します。

微分演算子の線形結合もサポートされています。たとえば、`op = Derivative(0) + λ Derivative(1)` は同次Robin BCに対応します。

高次の導関数も許可されており、Bスプライン基底の次数によってのみ制限されます。

## 例

```jldoctest RecombinedBSplineBasis
julia> B = BSplineBasis(BSplineOrder(4), -1:0.2:1)
13-element BSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]

julia> R_neumann = RecombinedBSplineBasis(B, Derivative(1))
11-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{1},)
 BCs right: (D{1},)

julia> R_robin = RecombinedBSplineBasis(B, Derivative(0) + 3Derivative(1))
11-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{0} + 3 * D{1},)
 BCs right: (D{0} + 3 * D{1},)
```

---

```
RecombinedBSplineBasis(B::BSplineBasis, ops)
RecombinedBSplineBasis(B::BSplineBasis, ops_left, ops_right)
```

複数の微分演算子に関連する同次BCを同時に満たす `RecombinedBSplineBasis` を構築します。

現在、次のケースがサポートされています：

1. 次数 `m` までのすべての導関数：

    `ops = (Derivative(0), ..., Derivative(m))`

    この境界条件は、元の基底から最初の `m + 1` のBスプラインを削除することによって得られます。

    たとえば、`(Derivative(0), Derivative(1))` が渡されると、基底は同時に両方の境界で同次DirichletおよびNeumann BCを満たします。結果として得られる基底は $ϕ_1 = b_3, ϕ_2 = b_4, …, ϕ_{N - 4} = b_{N - 2}$ です。
2. 上記の拡張で、最後に次数 `n` の追加の微分演算子を持つ：

    `ops = (Derivative(0), ..., Derivative(m), D(n))`

    演算子 `D(n)` は `Derivative` であるか、導関数の線形結合である可能性があります。唯一の制限は、その最大次数が `n ≥ m + 1` を満たす必要があることです。

    一例は、境界での同次Dirichlet BC $u = 0$ と導関数のRobin BC $u' + λ u'' = 0$ の組み合わせで、これは `ops = (Derivative(0), Derivative(1) + λ Derivative(2))` に対応します。
3. 一般化された自然境界条件：

    `ops = Natural()`

    これは `ops = (Derivative(2), Derivative(3), ..., Derivative(k ÷ 2))` に相当し、ここで `k` はスプラインの次数（偶数でなければなりません）です。詳細については [`Natural`](@ref) を参照してください。
4. 「自由」境界条件は、空のタプルまたは `nothing` を渡すことで単純に得られます：

    `ops = ()   ops = nothing`

    これは、再結合が行われないことを意味します。したがって、両方の境界で適用されると、結果として得られる基底は元の基底と同一になり、あまり有用ではありません。実際には、片方の境界でこれを適用し、もう一方の端で実際の境界条件で補完することが意味を持つ場合があります。

最初の2つのケースでは、微分演算子の次数は増加順でなければなりません。たとえば、`ops = (Derivative(1), Derivative(0))` はエラーになります。

## 例

```jldoctest RecombinedBSplineBasis
julia> ops = (Derivative(0), Derivative(1));


julia> R1 = RecombinedBSplineBasis(B, ops)
9-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{0}, D{1})
 BCs right: (D{0}, D{1})

julia> ops = (Derivative(0), Derivative(1) - 4Derivative(2));


julia> R2 = RecombinedBSplineBasis(B, ops)
9-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{0}, D{1} + -4 * D{2})
 BCs right: (D{0}, D{1} + -4 * D{2})

julia> R3 = RecombinedBSplineBasis(B, Natural())
11-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.0, 1.0, 1.0]
 BCs left:  (D{2},)
 BCs right: (D{2},)
```
