```
overapproximate(cap::Intersection{N,
                                  <:CartesianProductArray,
                                  <:AbstractPolyhedron},
                ::Type{<:CartesianProductArray}, oa) where {N}
```

有限個の集合の直積と多面体の交差を新しい直積で過大評価します。

### 入力

  * `cap`                   – 多面体と直積配列の遅延交差
  * `CartesianProductArray` – 目標集合タイプ
  * `oa`                    – 過大評価オプション

### 出力

`cpa` と `P` の交差を過大評価する `CartesianProductArray`。

### アルゴリズム

交差は、`P` で制約された `cpa` のブロック内でのみ計算する必要があります。したがって、まず制約されたブロックを低次元の直積配列に集め、それを `HPolytope` `X` に変換します。次に、`X` と対応する次元への `Y` の射影の交差を取ります。（この射影は純粋に構文的で正確です。）最後に、結果を再び分解し、影響を受けていない古いブロックと新しく計算されたブロックを組み合わせます。結果は、`X` と同じブロック構造を持つ `CartesianProductArray` です。
