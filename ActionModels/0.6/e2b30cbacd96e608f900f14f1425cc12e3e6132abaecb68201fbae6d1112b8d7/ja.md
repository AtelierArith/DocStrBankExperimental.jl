```
init_agent(action_model::Function; substruct::Any = nothing, parameters::Dict = Dict(), states::Union{Dict, Vector} = Dict(),
settings::Dict = Dict(), parameter_groups::Dict = Dict())
```

エージェントを初期化します。

action*modelは、アクションモデルのベクトルとしても指定できます: action*model::Vector{Function}。この場合、アクションモデルはエージェントの設定に保存されます。その場合は、関数'multiple_actions'を使用してください。

# 引数

  * 'action_model::Function': エージェントのアクションモデルを指定する関数。エージェントと単一の入力を引数として受け取り、アクションがサンプリングされる確率分布を返す任意の関数であることができます。
  * 'substruct::Any = nothing': 追加のパラメータと状態を含む構造体。この構造体はユーティリティ関数にも渡されます。高度な使用ガイドを確認してください。
  * 'parameters::Dict = Dict()': エージェントのパラメータを含む辞書。キーはパラメータ名（文字列または文字列のタプル）、値はパラメータの値です。
  * 'states::Union{Dict, Vector} = Dict()': エージェントの状態を含む辞書。キーは状態名（文字列または文字列のタプル）、値は初期状態の値です。状態名の文字列のベクトルでもかまいません。
  * 'settings::Dict = Dict()': エージェントの追加設定を含む辞書。キーは設定名、値は設定値です。
  * 'parameter_groups::Dict = Dict()': 共有パラメータを含む辞書。キーは共有パラメータの名前、値はその値を共有するパラメータのベクトルに続く共有パラメータの値です。

# 例

```julia

## バイナリ Rescorla-Wagner アクションモデルを持つエージェントを作成

## アクションモデル関数を作成

function binary*rescorla*wagner_softmax(agent::Agent, input::Union{Bool,Integer})

```

# パラメータを読み込む

learning*rate = agent.parameters["learning*rate"] action*precision = agent.parameters["action*precision"]

# 状態を読み込む

old_value = agent.states["value"]

# 値をシグモイド変換

old*value*probability = 1 / (1 + exp(-old_value))

# 新しい値の状態を取得

new*value = old*value + learning*rate * (input - old*value_probability)

# ソフトマックスを通してアクション確率を取得

action*probability = 1 / (1 + exp(-action*precision * new_value))

# 目標値の平均とパラメータからの標準偏差を持つベルヌーイ正規分布を作成

action*distribution = Distributions.Bernoulli(action*probability)

# 状態を更新

agent.states["value"] = new*value agent.states["value*probability"], 1 / (1 + exp(-new*value)) agent.states["action*probability"], action_probability

# 履歴に追加

push!(agent.history["value"], new*value) push!(agent.history["value*probability"], 1 / (1 + exp(-new*value))) push!(agent.history["action*probability"], action_probability)

return action_distribution ```

end

# 必要なパラメータを定義 parameters = Dict(     "learning*rate" => 1,     "action*precision" => 1,     ("initial", "value") => 0, )

# 必要な状態を定義 states = Dict(     "value" => missing,     "value*probability" => missing,     "action*probability" => missing, )

# エージェントを作成 agent = init*agent(     binary*rescorla*wagner*softmax,     parameters = parameters,     states = states,     settings = settings, )
