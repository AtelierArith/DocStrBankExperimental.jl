```
rstar(
    rng::Random.AbstractRNG=Random.default_rng(),
    classifier,
    samples::AbstractArray{<:Real};
    subset::Real=0.7,
    split_chains::Int=2,
    verbosity::Int=0,
)
```

`classifier`を用いて`samples`の$R^*$収束統計量を計算します。

`samples`は、形状が`(draws, [chains[, parameters...]])`の引き出しの配列です。

この実装は、LambertとVehtariによって説明されたアルゴリズム1および2の適応です。

`classifier`はMLJフレームワークの教師あり分類器でなければなりません（サポートされているモデルのリストについては[MLJドキュメント](@extref MLJ list_of_supported_models)を参照してください）。各チェーンからのサンプルの`subset`で訓練されます。各チェーンは、チェーン内の収束を追加で確認するために`split_chains`個の別々のチェーンに分割されます。分類器の訓練は、`verbosity`レベルを調整することで確認できます。

分類器が決定論的である場合、すなわちクラスを予測する場合、$R^*$統計量の値が返されます（アルゴリズム1）。分類器が確率的である場合、すなわちクラスの確率を出力する場合、$R^*$統計量のスケーリングされたポアソン-二項分布が返されます（アルゴリズム2）。

!!! note
    統計量の正確性は、統計量内で内部的に使用される`classifier`の収束に依存します。


# 例

```jldoctest rstar; setup = :(using Random; Random.seed!(101))
julia> using MLJBase, MLJIteration, EvoTrees, Statistics, StatisticalMeasures

julia> samples = fill(4.0, 100, 3, 2);
```

確率的分類器を用いて$R^*$統計量の分布（アルゴリズム2）を計算できます。たとえば、`nrounds = 100`の逐次スタックされた木と学習率`eta = 0.05`を持つ勾配ブースト木モデルを使用できます：

```jldoctest rstar
julia> model = EvoTreeClassifier(; nrounds=100, eta=0.05);

julia> distribution = rstar(model, samples);

julia> round(mean(distribution); digits=2)
1.0f0
```

ただし、`nrounds`は早期停止に基づいて決定することが推奨されます。MLJフレームワークでは、次のようにしてこれを達成できます（追加の説明については[MLJドキュメント](@extref MLJ Controlling-Iterative-Models)を参照してください）：

```jldoctest rstar
julia> model = IteratedModel(;
           model=EvoTreeClassifier(; eta=0.05),
           iteration_parameter=:nrounds,
           resampling=Holdout(),
           measures=log_loss,
           controls=[Step(5), Patience(2), NumberLimit(100)],
           retrain=true,
       );

julia> distribution = rstar(model, samples);

julia> round(mean(distribution); digits=2)
1.0f0
```

決定論的分類器の場合、単一の$R^*$統計量（アルゴリズム1）が返されます。決定論的分類器は、たとえばモードを予測することによって確率的分類器から導出することもできます。MLJでは、これはモデルの[パイプライン](@extref MLJ Pipeline_MLJBase)に対応します。

```jldoctest rstar
julia> evotree_deterministic = Pipeline(model; operation=predict_mode);

julia> value = rstar(evotree_deterministic, samples);

julia> round(value; digits=2)
1.0
```

# 参考文献

Lambert, B., & Vehtari, A. (2020). $R^*$: A robust MCMC convergence diagnostic with uncertainty using decision tree classifiers.
