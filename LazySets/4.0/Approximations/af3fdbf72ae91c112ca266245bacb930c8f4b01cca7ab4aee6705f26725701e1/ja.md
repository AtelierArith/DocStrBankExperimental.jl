```
decompose(S::LazySet{N},
          partition::AbstractVector{<:AbstractVector{Int}},
          block_options) where {N}
```

高次元集合を指定された部分空間に対する射影のオーバー近似の直積に分解します。

### 入力

  * `S`             – 集合
  * `partition`     – ブロックのベクトル（すなわち整数のベクトルのベクトル）（以下のノートを参照）
  * `block_options` – `partition`内のブロックインデックスから対応するオーバー近似オプションへのマッピング；`[⋅]`を介してのアクセスのみが必要です（ただし、以下のノートも参照）

### 出力

低次元の近似射影を含む`CartesianProductArray`。

### アルゴリズム

各ブロックに対して特定の`project`メソッドが呼び出され、対応するオーバー近似オプションに基づいてディスパッチされます。

### ノート

引数`partition`にはいくつかの説明が必要です。通常、ブロックのリストは集合$\{1, …, n\}$の分割を形成する必要があり、これは連続したブロックのリストとして表され、$n$は集合`S`の周囲の次元です。

ただし、技術的にはブロックが連続していない、ブロックが欠けている、ブロックが複数回出現する、またはブロックが重なっている場合でも問題はありません。そのような場合、結果の集合は注意して解釈する必要があります（例えば、必ずしも`S`のオーバー近似にはならない）。

便宜上、引数`block_options`はマッピングの代わりに単一のオプションとして与えることもでき、その場合はすべてのブロックのオプションとして解釈されます。

### 例

引数`block_options`は異なるオプションをサポートします：ターゲット集合、精度の度合い、テンプレート方向を指定できます。以下に例を示します。

```jldoctest decompose_examples
julia> S = Ball2(zeros(4), 1.0);  # 分解される集合（4D 2ノルム単位球）

julia> P2d = [1:2, 3:4];  # サイズ2の2つのブロックを持つ分割

julia> P1d = [[1], [2], [3], [4]];  # サイズ1の4つのブロックを持つ分割
```

#### 異なる集合タイプ

制約表現の多角形を使用して分解できます：

```jldoctest decompose_examples
julia> Y = decompose(S, P2d, HPolygon);

julia> all(ai isa HPolygon for ai in Y)
true
```

1D部分空間への分解には`Interval`を使用できます：

```jldoctest decompose_examples
julia> Y = decompose(S, P1d, Interval);

julia> all(ai isa Interval for ai in Y)
true
```

ただし、異なるブロックに対して異なる集合タイプを指定する必要がある場合、これまでに提示されたインターフェースは適用されません。異なるブロック近似のための高度な入力については、以下の段落を参照してください。

#### 分解の精緻化：$ε$-近似

$$
ε
$$

オプションを使用して分解を精緻化し、より正確な結果を得ることができます。`Approximations`モジュールの[Iterative refinement](@ref)アルゴリズムを使用します。

これを示すために、上記の集合`S`を再度考えます。2つの2D多角形に分解します。小さい$ε$を使用すると、より良い精度が得られ、したがって各2D分解における制約が増えます。以下の例では、最初のブロックの制約の数を見ます。

```jldoctest decompose_examples
julia> d(ε, bi) = array(decompose(S, P2d, (HPolygon => ε)))[bi]
d (generic function with 1 method)

julia> [length(constraints_list(d(ε, 1))) for ε in [Inf, 0.1, 0.01]]
3-element Vector{Int64}:
  4
  8
 32
```

#### 分解の精緻化：テンプレート多面体

分解を精緻化する別の方法は、テンプレート多面体を使用することです。アイデアは、テンプレート方向のセットを指定し、次に各ブロックで与えられた入力集合のサポート関数をテンプレート方向に沿って評価することによって得られる多面体オーバー近似を計算することです。

例えば、集合`S`の8角形2D近似は次のように得られます：

```jldoctest decompose_examples
julia> B = decompose(S, P2d, OctDirections);

julia> length(B.array) == 2 && all(dim(bi) == 2 for bi in B.array)
true
```

利用可能なテンプレート方向については[Template directions](@ref)を参照してください。上記の多角形の$ε$-近似とは対照的に、この方法は任意のサイズのブロックに適用できます。

```jldoctest decompose_examples
julia> B = decompose(S, [1:4], OctDirections);

julia> length(B.array) == 1 && dim(B.array[1]) == 4
true
```

#### 異なるブロック近似のための高度な入力

各ブロックに対して均一に近似オプションを定義する代わりに、異なるブロックに対して異なる近似を定義できます。この目的のために、引数`block_options`はブロックインデックス（分割内）から対応する近似オプションへのマッピングでも構いません。

例えば、最初のブロックを`Hyperrectangle`で近似し、2番目のブロックを$ε$-近似（$ε = 0.1$）で近似することができます：

```jldoctest decompose_examples
julia> res = array(decompose(S, P2d, Dict(1 => Hyperrectangle, 2 => 0.1)));

julia> typeof(res[1]), typeof(res[2])
(Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}, HPolygon{Float64, Vector{Float64}})
```
