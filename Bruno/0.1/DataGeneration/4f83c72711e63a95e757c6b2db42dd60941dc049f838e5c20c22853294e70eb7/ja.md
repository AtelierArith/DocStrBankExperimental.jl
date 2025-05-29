```
BootstrapInput(input_data, bootstrap_method::<:TSBootMethod; kwargs...)
BootstrapInput{T <: TSBootMethod}(; kwargs...)
```

ブロックブートストラップのタイプ T を実行するために必要なパラメータを含んでおり、`makedata()` 関数で使用されます。T は TSBootMethod の任意のサブタイプ（Stationary、MovingBlock、または CircularBlock）であることができます。

## キーワード引数

  * `input_data`: 再サンプリングするデータ。1-D 配列である必要があります。
  * `bootstrap_method`: 使用する時系列ブートストラップのタイプ。TSBootMethod のサブタイプである必要があります。
  * `n`: 再サンプリングされた出力データのサイズ。デフォルト: 100
  * `block_size`: 使用するブロックサイズ。デフォルトは `opt_block_length()` を使用した最適なブロック長です。

## 例

```julia
input_data = [1,2,4,3,5,7,6,3];
kwargs = Dict(:n=>20);
input1 = BootstrapInput(input_data, Stationary; kwargs...)

kwargs = Dict(:input_data=>input_data, :n=>20, :block_size=>4);
input2 = BootstrapInput{MovingBlock}(;kwargs...)
```
