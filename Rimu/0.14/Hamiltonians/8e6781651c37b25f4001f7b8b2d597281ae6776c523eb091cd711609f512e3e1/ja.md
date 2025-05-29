```
get_all_blocks(h::Union{HOCartesianContactInteractions,HOCartesianEnergyConservedPerDim};
    target_energy = nothing,
    max_energy = nothing,
    max_blocks = nothing,
    method = :vertices,
    kwargs...) -> df
```

`h`のすべての異なるブロックを見つけます。次の列を持つ`DataFrame`を返します。

  * `block_id`: 見つかった順にブロックのインデックス
  * `block_E0`: ブロック内のすべての要素の非相互作用エネルギー
  * `block_size`: ブロック内の要素の数
  * `addr`: 例えば[`BasisSetRepresentation`](@ref)を使用してブロックを生成する最初のアドレス
  * `indices`: 生成アドレス`addr`を再生成するためのモードインデックスのタプル; この場合、例えば`BoseFS(M; indices .=> 1)`を使用します。これは、`DataFrame`がファイルから読み込まれるときに便利です。なぜなら、`Arrow.jl`がカスタムタイプを`NamedTuple`に変換するからです。
  * `t_basis`: 各ブロックの基底を生成するのにかかる時間

キーワード引数:

  * `target_energy`: この非相互作用エネルギーを持つブロックのみが見つかります
  * `max_energy`: この値未満の非相互作用エネルギーを持つブロックのみが見つかります
  * `max_blocks`: この数のブロックを見つけた後に終了します
  * `method`: 量子数のタプルを列挙する方法として`:vertices`と`:comb`の間で選択します
  * `save_to_file=nothing`: 設定されている場合、新しいブロックが見つかるたびにブロックを記録する`DataFrame`が保存されます
  * 追加の`kwargs`: ブロックエネルギーを比較するために`isapprox`に渡されます。異方性トラップに便利です

注意: `h`が`block_by_level = false`オプションで構築された場合、ブロックシード`addr`はパリティによって決定されます。この場合、ブロックは生成されず、`t_basis`はゼロになり、`block_size`は推定値になります。適切な`filter`を使用して[`BasisSetRepresentation`](@ref)にシードアドレスを渡してブロックを生成します。
