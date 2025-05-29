```
PredictiveModel(networks, input_output_map, input_size, output_size)
```

Fluxモデルと入力/出力情報からAppDrivenLearningモジュールの予測（予測）モデルを作成します。

...

# 引数

  * `networks`: 使用するFluxモデルの配列。
  * `input_output_map::Vector{Dict{Vector{Int}, Vector{Int}}}`: モデルが適用される入力インデックスから出力インデックスへのマッピングの配列で、ネットワークと同じ順序です。
  * `input_size::Int`: 入力ベクトルのサイズ。
  * `output_size::Int`: 出力ベクトルのサイズ。 ...

# 例

```
julia> pred_model = PredictiveModel(
        [Flux.Dense(1 => 1), Flux.Dense(3 => 2)],
        [
            Dict([1] => [1], [1] => [2]),
            Dict([1,2,3] => [3,4], [1,4,5] => [5,6])
        ],
        5,
        6
    );
```
