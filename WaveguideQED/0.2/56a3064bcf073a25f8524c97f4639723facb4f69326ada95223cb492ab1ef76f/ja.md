```
detect_single_click(ψ,detector::Detector,projection)
detect_single_click(ψ,detector::Detector)
```

ビームスプリッタ操作と、その後の検出イベントが`detector`で定義された状態`ψ`の後に`projection`を観測する確率を計算します。

# 引数

  * `ψ`は[`LazyTensorKet`](@ref)または[`LazySumKet`](@ref)のいずれかであり、ビームスプリッタと検出が適用される状態です。
  * `detector`はビームスプリッタとその後の検出操作を定義します。定義方法の詳細については[`Detector`](@ref)を参照してください。
  * `projection`が指定されている場合は、測定後の状態に投影する[`LazyTensorKet`](@ref)または[`LazySumKet`](@ref)です。投影が指定されていない場合は、[`get_all_projectors`](@ref)を使用して、すべての可能な投影の組み合わせを適用することによって、検出器がクリックする総確率が与えられます。

# 戻り値

  * `projection`が指定されている場合、検出器がクリックし、`projection`で定義された状態にある確率を返します。
  * `projection`が指定されていない場合、検出器がクリックする総確率を返します（ダブルクリックの場合は[`detect_double_click`](@ref)を使用してください）。これは、[`get_all_projectors`](@ref)を使用して、波導内のゼロ光子でのすべての可能な投影を適用することによって得られます。

使用方法の例については、[Beamsplitter](https://mabuni1998.github.io/WaveguideQED/dev/detection_example/)を参照してください。
