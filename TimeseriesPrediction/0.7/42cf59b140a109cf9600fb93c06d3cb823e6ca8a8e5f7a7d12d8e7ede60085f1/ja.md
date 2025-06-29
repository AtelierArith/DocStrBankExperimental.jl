```
light_cone_embedding(s, γ, τ, r0, c, bc=PeriodicBoundary()) → embedding
```

[`SpatioTemporalEmbedding`](@ref) インスタンスを作成し、*光円錐*の概念に基づいて点の空間的および時間的隣接点を含めます。

この埋め込みは `s` からのデータと共に使用されます。

## 説明

情報は瞬時に移動するのではなく、有限の速度 `c ≥ 0.0` で移動します。このコンストラクタは、情報の速度 `c` に基づいて予測に影響を与えることができる、空間と時間のすべての点を含む円錐状の埋め込みを作成します。 `γ` は埋め込みに含める過去の時間ステップの数であり、過去の各ステップには追加の遅延時間 `τ::Int` があります。 `γ=0` は現在のみを使用することに対応します。 `r0` は円錐の頂点での初期半径、すなわち現在の影響半径です。 `bc` は境界条件です。

光円錐の半径は次のように進化します: `r_i = i*τ*c + r0` で、各ステップ `i ∈ 0:γ` に対して。

例えば、`γ = 1, τ = 2, r0 = 1` の一次元システムでは、埋め込みは次のようになります（`□` = 現在の点（埋め込みに*定義上*含まれる）、`o` は [`temporalprediction`](@ref) を使用して予測される点、`x` = 埋め込みに含まれる点、`.` = 埋め込みに含まれない点）

```
time  | c = 1.0               | c = 2.0               | c = 0.0

n + 1 | ..........o.......... | ..........o.......... | ..........o..........
n     | .........x□x......... | .........x□x......... | .........x□x.........
n - 1 | ..................... | ..................... | .....................
n - τ | .......xxxxxxx....... | .....xxxxxxxxxx...... | .........xxx.........
```

この例に加えて、公式ドキュメントでは、2次元の光円錐のプロットを生成する関数 `explain_light_cone` を示しています（理解するのに最適です！）。
