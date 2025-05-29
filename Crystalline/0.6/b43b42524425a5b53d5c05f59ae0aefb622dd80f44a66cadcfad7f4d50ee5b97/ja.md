```
remap_to_kstar(
    lgirs::AbstractVector{LGIrrep{D}},
    kv′::KVec{D},
    coset_representatives::AbstractVector{SymOperation{D}}
    ) --> Collection{LGIrrep{D}}
```

与えられた `LGIrrep` の集合 `lgirs` が **k**-ベクトル `kv` で定義されている場合、irrep データを異なる **k**-ベクトル `kv′` に再マップします。

再マッピングは、操作 `g` を特定することによって行われます。すなわち、`kv′ = g * kv` であり、`g` は `lgirs` の空間群に属します（より正確には、空間群の小群のコセット代表の中から）。元の irreps $D(h)$ は、$h$ が `kv` の小群にあるとき、$D'(h') = D(h) = D(g⁻¹h'g)$ に従って変換されます。ここで、$h'$ は `kv'` の小群からのものです。

コセット代表はオプションの引数として指定でき、再計算を避け、`g` の関連する計算を簡素化します。コセット代表は `kv` の星を生成します。
