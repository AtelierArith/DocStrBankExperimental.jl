```julia
struct Reaction{S, T}
```

1つの化学反応。

# フィールド

  * `rate`: 反応速度関数（質量作用項を除く）。
  * `substrates`: 反応基質。
  * `products`: 反応生成物。
  * `substoich`: 反応物の化学量論係数。
  * `prodstoich`: 生成物の化学量論係数。
  * `netstoich`: 反応によって変化するすべての種のネット化学量論係数。
  * `only_use_rate`: `rate`が質量作用項で掛け算されて反応速度法則を与える場合は`false`（デフォルト）。`rate`が完全な反応速度法則を表す場合は`true`。
  * `metadata`: 反応が化学ランジュバン方程式の特定のノイズスケーリング表現を持つ場合など、追加データを含む。

# 例

```julia
using Catalyst
t = default_t()
@parameters k[1:20]
@species A(t) B(t) C(t) D(t)
rxs = [Reaction(k[1], nothing, [A]),            # 0 -> A
       Reaction(k[2], [B], nothing),            # B -> 0
       Reaction(k[3],[A],[C]),                  # A -> C
       Reaction(k[4], [C], [A,B]),              # C -> A + B
       Reaction(k[5], [C], [A], [1], [2]),      # C -> A + A
       Reaction(k[6], [A,B], [C]),              # A + B -> C
       Reaction(k[7], [B], [A], [2], [1]),      # 2B -> A
       Reaction(k[8], [A,B], [A,C]),            # A + B -> A + C
       Reaction(k[9], [A,B], [C,D]),            # A + B -> C + D
       Reaction(k[10], [A], [C,D], [2], [1,1]), # 2A -> C + D
       Reaction(k[11], [A], [A,B], [2], [1,1]), # 2A -> A + B
       Reaction(k[12], [A,B,C], [C,D], [1,3,4], [2, 3]),          # A+3B+4C -> 2C + 3D
       Reaction(k[13], [A,B], nothing, [3,1], nothing),           # 3A+B -> 0
       Reaction(k[14], nothing, [A], nothing, [2]),               # 0 -> 2A
       Reaction(k[15]*A/(2+A), [A], nothing; only_use_rate=true), # A -> 0 with custom rate
       Reaction(k[16], [A], [B]; only_use_rate=true),             # A -> B with custom rate.
       Reaction(k[17]*A*exp(B), [C], [D], [2], [1]),              # 2C -> D with non constant rate.
       Reaction(k[18]*B, nothing, [B], nothing, [2]),             # 0 -> 2B with non constant rate.
       Reaction(k[19]*t, [A], [B]),                                # A -> B with non constant rate.
       Reaction(k[20]*t*A, [B,C], [D],[2,1],[2])                  # 2A +B -> 2C with non constant rate.
  ]
```

ノート：

  * `nothing`は、反応物や生成物がない反応を示すために使用できます。この場合、対応する化学量論ベクトルも`nothing`に設定する必要があります。
  * 3引数形式は、すべての反応物および生成物の化学量論係数が1であると仮定します。
