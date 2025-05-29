```julia
sketch(
    A,
    X;
    force_single_batch,
    batch_size,
    out_dic,
    kwargs...
)

```

`X`のスケッチをスケッチ演算子`A`に対して返します。`force_single_sketch`が`true`に設定されていない限り、スケッチは`X`を小さなバッチに分割し、各バッチを個別にスケッチすることによって計算され、メモリ効率が向上します。バッチサイズは`BatchIterators.choose_batchsize`を使用して選択されますが、特に以下の制約を使用できます：

  * `maxmemGB`: スケッチされたバッチの最大メモリ；
  * `maxbatchsize`: バッチのサンプルの最大数。
  * `batch_size`: 使用する正確なバッチサイズ。
  * `force_single_batch`: すべてのデータを1つのバッチとしてスケッチします。
