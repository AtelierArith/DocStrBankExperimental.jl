```
LaSROptions(;kws...) <: SymbolicRegression.AbstractOptions
```

`equation_search`や他の関数のオプションを構築します。また、SymbolicRegression.Optionsも参照してください。

# 引数

  * `use_llm::Bool`: LLM推論を使用するかどうか。(デフォルト: false)
  * `use_concepts::Bool`: 候補プログラムを自然言語の概念に要約し、それらの概念を使用して検索をガイドするかどうか（すなわち、FunSearchの特殊化）。(デフォルト: false)   注: `use_llm`がfalseの場合、`use_concepts`は無視されます。
  * `use_concept_evolution::Bool`: 各イテレーションの後に概念を進化させるかどうか。(デフォルト: false)   注: `use_concepts`がfalseの場合、`use_concept_evolution`は無視されます。
  * `mutation_weights::LaSRMutationWeights`: 突然変異演算子（例: `llm_mutate`, `llm_randomize`）のための非正規化された突然変異重み。
  * `llm_operation_weights::LLMOperationWeights`: LLMベースの交差とシンボリック交差を使用する確率の正規化された値。
  * `num_pareto_context::Int64`: 要約のためにパレートフロンティアからサンプリングする方程式の数。
  * `num_generated_equations::Int64`: 各イテレーションでLLMから生成する新しい方程式の数。
  * `num_generated_concepts::Int64`: 各イテレーションでLLMから生成する新しい概念の数。
  * `num_concept_crossover::Int64`: 概念交差のために追加する概念の数。(デフォルト: 2)
  * `max_concepts::UInt32`: 概念ライブラリに保持する最大概念数。(デフォルト: 30)
  * `is_parametric::Bool`: LaSRからパラメトリック方程式をサンプリングすることを許可する特別なフラグ。(デフォルト: false)
  * `llm_context::AbstractString`: LLMに渡される自然言語のヒントまたはコンテキスト文字列。
  * `variable_names::Union{Dict,Nothing}`: シンボリック変数名をドメインに意味のある名前にマッピングするもの。(デフォルト: nothing)
  * `prompts_dir::AbstractString`: LLMのためのゼロショットプロンプトの場所。より良いパフォーマンスのためにこれらのプロンプトをあなたのドメインに特化させてください。(デフォルト: "prompts/")
  * `idea_database::Vector{AbstractString}`: LLMのシード用の自然言語の概念「アイデア」のリスト。(デフォルト: [])
  * `api_key::AbstractString`: OpenAI互換サーバーのAPIキー。必須。
  * `model::AbstractString`: OpenAI互換サーバーのLLMモデル名。必須。
  * `api_kwargs::Dict`: LLMのAPIのための追加のキーワード引数。エンドポイントを指定するために`url::AbstractString`を含める必要があります。(デフォルト: `Dict("url" => "...")`)

      * 例えば: `Dict("url" => "http://localhost:11440/v1", "max_tokens" => 1000)`
  * `http_kwargs::Dict`: HTTPリクエストのための追加のキーワード引数。

      * `retries::Int`: リトライの回数。(デフォルト: 3)
      * `readtimeout::Int`: 読み取りタイムアウト（秒）。(デフォルト: 3600)
  * `verbose::Bool`: 各LLM呼び出しのためにトークンと追加のデバッグ情報を印刷するかどうか。(デフォルト: true)
