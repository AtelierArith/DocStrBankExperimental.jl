```
deactivate_overwritten_control_points!(
    control_points::LocallyRefinedControlPoints,
    local_refinement_level::Integer)::Nothing
```

効果が完全に上書きされた制御点を無効にします。手順は次のように進行します。

ローカルリファインメントを処理するための「前方」計算は次のようになります：

`B = (O₂ ∘ L ∘ O₁)(A)`、

ここで：

  * `A` は `local_refinement_level` における制御点グリッドです
  * `B` は `local_refinement_level + 1` における制御点グリッドです
  * `O₁` は `local_refinement_level` におけるアクティブな制御点の上書き操作です
  * `L` は指定された次元に沿ってリファインメント行列で乗算する線形操作です
  * `O₂` は `local_refinement_level + 1` におけるアクティブな制御点の上書き操作です

`O₁` の任意の上書き要素の効果が最終配列にまだ存在するかどうかを判断するために、次の計算を行います：

`A = (L* ∘ O₂)(B)`、

ここで：

  * `B` は特別な数 `Flag` で初期化され、これはこの数が関連しているかどうかを示す単純なブールラッパーです。`B` はすべて `Flag(true)` で初期化されます
  * `O₂` の上書き値はすべて `Flag(false)` で初期化されます
  * `L*` は `L` の随伴バージョンです

この計算の後、`A` の `O₁` の上書き位置で各数が `B` に対してまだ効果を持っているかどうかを読み取ることができます。
