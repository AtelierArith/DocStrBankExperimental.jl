```
apply(o::ITensor, ψ::Union{MPS, MPO}, [ns::Vector{Int}]; kwargs...)
product([...])
```

演算子 `o` と MPS/MPO `ψ` の積を取得します。ここで、演算子はサイト `ns` に適用されます。`ns` が指定されていない場合、サイトは `o` と `ψ` のサイトインデックス間の共通インデックスによって決定されます。

`ns` が非連続の場合、MPS のサイトは連続になるように移動されます。デフォルトでは、サイトは元の位置に戻されます。キーワード引数 `move_sites_back` を false に設定することで、元の位置に戻さずにそのままにしておくことができます。

# キーワード

  * `cutoff::Real`: 特異値切断のカットオフ。
  * `maxdim::Int`: 最大 MPS/MPO 次元。
  * `apply_dag::Bool = false`: ゲートとゲートのダガーを適用します（MPO の進化にのみ関連）。
  * `move_sites_back::Bool = true`: ITensor が MPS または MPO に適用された後、MPS または MPO のサイトを元の位置に戻します。
