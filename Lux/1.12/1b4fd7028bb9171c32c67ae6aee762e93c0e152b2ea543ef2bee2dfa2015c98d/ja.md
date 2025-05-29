```
Recurrence(cell;
    ordering::AbstractTimeSeriesDataBatchOrdering=BatchLastIndex(),
    return_sequence::Bool=false)
```

再帰セル（[`RNNCell`](@ref)、[`LSTMCell`](@ref)、[`GRUCell`](@ref)のような）をラップして、入力のシーケンス全体に対して自動的に操作します。

!!! warning "Relation to `Flux.Recur`"
    これは`Flux.Recur`とは完全に異なります。`cell`を状態を持つものにするのではなく、入力のシーケンス全体に対して一度に操作できるようにします。`Flux.Recur`に似た機能については[`StatefulRecurrentCell`](@ref)を参照してください。


## 引数

  * `cell`: 再帰セル。再帰セルの入力/出力がどのように構造化されるべきかについては、[`RNNCell`](@ref)、[`LSTMCell`](@ref)、[`GRUCell`](@ref)を参照してください。

## キーワード引数

  * `return_sequence`: `true`の場合、出力の全シーケンスを返し、そうでない場合は最後の出力のみを返します。デフォルトは`false`です。
  * `ordering`: 入力のバッチと時間次元の順序。デフォルトは`BatchLastIndex()`です。代わりに`TimeLastIndex()`に設定することもできます。

# 拡張ヘルプ

## 入力

  * `x`が

      * タプルまたはベクター: 各要素が`cell`に順次供給されます。
      * 配列（ベクターを除く）: 最後から2番目の次元に沿ってスライスされ、各スライスが`cell`に順次供給されます。

## 戻り値

  * シーケンス全体に対する`cell`の出力。
  * `cell`の状態を更新します。

!!! tip
    Tensorflowのようなフレームワークには、連続的に構成されたRNNセルを処理するための[`StackedRNNCells`](https://www.tensorflow.org/api_docs/python/tf/keras/layers/StackedRNNCells)の特別な実装があります。Luxでは、複数の`Recurrence`ブロックを`Chain`に単純にスタックすることで同じことを達成できます。

    ```
    Chain(
        Recurrence(RNNCell(inputsize => latentsize); return_sequence=true),
        Recurrence(RNNCell(latentsize => latentsize); return_sequence=true),
        :
        x -> stack(x; dims=2)
    )
    ```

    このトピックに関する議論については、https://github.com/LuxDL/Lux.jl/issues/472を参照してください。


```
