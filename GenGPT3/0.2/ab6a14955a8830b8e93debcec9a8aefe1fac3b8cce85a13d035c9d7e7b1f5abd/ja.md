```
GPT3ImportanceSampler(;
    model_gf::MultiGPT3GF = MultiGPT3GF(),
    proposal_gf::MultiGPT3GF = model_gf,
    validator::V = nothing,
    max_samples::Union{Int, Nothing} = nothing,
    cache_traces::Bool = false,
)
```

GPT-3モデルからの重要度サンプリングを行う生成関数で、[`MultiGPT3GF`](@ref)生成関数をモデルと提案として使用します。引数`(n_samples, model_prompt, proposal_prompt)`で呼び出され、`n_samples`は引き出すサンプルの数、`model_prompt`はモデルに使用するプロンプト、`proposal_prompt`は提案に使用するプロンプトです。

`n_samples`サンプルが提案から引き出された後、モデルを使用して各サンプルのスコアを計算し、重要度重みが計算されます。重要度重みに従って単一のサンプルが選択され、生成関数の出力として返されます。`output`と`chosen`インデックスは、トレースの選択マップの一部です。

# 引数

  * `model_gf::MultiGPT3GF`: モデルに使用する生成関数。
  * `proposal_gf::MultiGPT3GF`: 提案に使用する生成関数。
  * `validator`: サンプル出力に使用するバリデータ関数。提供された場合、有効なサンプルの数が`n_samples`に等しくなるまでサンプルが引き出されます。`nothing`に設定された場合、バリデーションは行われません。
  * `max_samples::Union{Int, Nothing}`: バリデーションが有効な場合、提案から引き出す最大サンプル数。`nothing`に設定された場合、最大は強制されません。
  * `cache_traces::Bool`: トレースをキャッシュするかどうか。`true`に設定された場合、トレースは辞書にキャッシュされ、同じ引数が提供された場合に再利用されます。
