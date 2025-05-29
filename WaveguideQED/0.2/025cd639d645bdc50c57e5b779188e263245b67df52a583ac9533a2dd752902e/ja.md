```
detect_double_click(ψ,detector1,detector2,projection)
detect_double_click(ψ,detector1,detector2)
```

ビームスプリッタ操作の後、状態 `ψ` に対して `detector1` と `detector2` で定義された2つの検出イベントの後に `projection` を観測する確率を計算します。

# 引数

  * `ψ` は [`LazyTensorKet`](@ref) または [`LazySumKet`](@ref) のいずれかであり、ビームスプリッタと検出が適用される状態です。
  * `detector1` は最初のビームスプリッタとその後の検出操作を定義します。定義方法の詳細については [`Detector`](@ref) を参照してください。
  * `detector2` は2番目のビームスプリッタとその後の検出操作を定義します。定義方法の詳細については [`Detector`](@ref) を参照してください。
  * `projection` が指定されている場合は、測定後の状態に射影する [`LazyTensorKet`](@ref) または [`LazySumKet`](@ref) です。射影が指定されていない場合は、[`get_all_projectors`](@ref) を使用して、すべての可能な射影の組み合わせを適用することによって、検出器がクリックする総確率が与えられます。

# 戻り値

  * `projection` が指定されている場合: `detector1` と `detector2` がクリックし、`projection` で定義された状態にある確率を返します。
  * `projection` が指定されていない場合: [`get_all_projectors`](@ref) を使用して、波導内のゼロ光子でのすべての可能な射影を適用することによって、`detector1` と `detector2` がクリックする総確率を返します。

使用方法の例については [Beamsplitter](https://mabuni1998.github.io/WaveguideQED/dev/detection_example/) を参照してください。
