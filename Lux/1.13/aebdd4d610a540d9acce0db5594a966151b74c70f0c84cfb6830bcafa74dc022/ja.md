```
BidirectionalRNN(cell::AbstractRecurrentCell,
    backward_cell::Union{AbstractRecurrentCell, Nothing}=nothing;
    merge_mode::Union{Function, Nothing}=vcat,
    ordering::AbstractTimeSeriesDataBatchOrdering=BatchLastIndex())
```

双方向RNNラッパー。

## 引数

  * `cell`: 再帰セル。再帰セルの入力/出力がどのように構造化されるべきかについては、[`RNNCell`](@ref)、[`LSTMCell`](@ref)、[`GRUCell`](@ref)を参照してください。
  * `backward_cell`: オプションの逆方向再帰セル。`backward_cell`が`nothing`の場合、`cell`引数として渡されたrnnレイヤーインスタンスが自動的に逆方向レイヤーを生成するために使用されます。`backward_cell`の`in_dims`は`cell`の`in_dims`と一致している必要があります。

## キーワード引数

  * `merge_mode`: 前方および後方RNNの出力を結合するための関数。デフォルト値は`vcat`です。`nothing`の場合、出力は結合されません。
  * `ordering`: 入力のバッチおよび時間次元の順序。デフォルトは`BatchLastIndex()`です。代わりに`TimeLastIndex()`に設定することもできます。

# 拡張ヘルプ

## 入力

  * `x`が

      * タプルまたはベクター: 各要素が順次`cell`に供給されます。
      * 配列（ベクターを除く）: 最後から2番目の次元に沿ってスライスされ、各スライスが順次`cell`に供給されます。

## 戻り値

  * シーケンス全体に対する`cell`と`backward_cell`の結合出力。
  * `cell`と`backward_cell`の状態を更新します。

## パラメータ

  * `cell`と`backward_cell`を含む`NamedTuple`。

## 状態

  * `cell`と`backward_cell`と同じ。
