```
Consistent(predictions::AbstractVector)
```

`predictions` と対応するターゲットのリサンプリングに使用できるオブジェクトを作成します。

予測のセットは、次のようなベクトルとして提供する必要があります。

  * 確率、
  * 合計が 1 になる確率のベクトル、
  * またはサンプリング可能な分布。

一貫性のあるリサンプリングは、[`Random`](https://docs.julialang.org/en/v1/stdlib/Random/) のドキュメントに記載されているように、`rand` および `rand!` を使用して実行できます。

# 例

```jldoctest
julia> predictions = rand(100);

julia> consistent = Consistent(predictions);

julia> rand(consistent) isa Tuple{Float64,Bool}
true

julia> first(rand(consistent)) in predictions
true
```

!!! note
    `Random.Sampler` を使用して、エイリアス テーブルを構築することにより、複数のサンプルの生成に最適化されたサンプラーを作成できます:

    ```jldoctest
    julia> using Random: Sampler, GLOBAL_RNG

    julia> sampler = Sampler(GLOBAL_RNG, Consistent(rand(100)));

    julia> rand(sampler) isa Tuple{Float64,Bool}
    true
    ```

    ただし、サンプル数が少ない場合、セットアップコストが改善されたサンプリング効率を上回る可能性があります。


!!! note
    複数のサンプルは、予測と対応するターゲットのタプルの配列として返されます。代わりに予測とターゲットの配列のタプルを希望する場合は、[StructArrays](https://github.com/JuliaArrays/StructArrays.jl) のようなパッケージを使用して、インプレースサンプリングを実行できます:

    ```jldoctest
    julia> using StructArrays, Random

    julia> predictions = Vector{Float64}(undef, 100);

    julia> targets = Vector{Bool}(undef, 100);

    julia> rand!(StructVector((predictions, targets)), Consistent(rand(100)));
    ```


# 参考文献

Bröcker, J. and Smith, L.A., 2007. [信頼性ダイアグラムの信頼性を高める](https://doi.org/10.1175/WAF993.1). Weather and forecasting, 22(3), pp. 651-661.
