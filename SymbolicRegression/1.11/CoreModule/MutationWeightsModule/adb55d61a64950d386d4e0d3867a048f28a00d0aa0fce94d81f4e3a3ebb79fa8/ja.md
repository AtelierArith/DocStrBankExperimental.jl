```
AbstractMutationWeights
```

シンボリック回帰フレームワークにおける突然変異重み構造のインターフェースを定義する抽象型です。`AbstractMutationWeights`のサブタイプは、突然変異プロセス中に異なる突然変異操作がどのくらいの頻度で発生するかを指定します。

`AbstractMutationWeights`をサブタイプ化して独自の突然変異操作を定義することで、カスタム突然変異重みタイプを作成できます。さらに、`sample_mutation`関数をオーバーロードして、カスタム突然変異タイプからのサンプリングを処理することができます。

# 使用法

新しい突然変異タイプを持つカスタム突然変異重み付けスキームを作成するには、`AbstractMutationWeights`の新しいサブタイプを定義し、必要なフィールドを実装します。以下は、デフォルト値を持つ構造体を定義するために`Base.@kwdef`を使用した例です：

```julia
using SymbolicRegression: AbstractMutationWeights

# デフォルト値を持つカスタム突然変異重みを定義
Base.@kwdef struct MyMutationWeights <: AbstractMutationWeights
    mutate_constant::Float64 = 0.1
    mutate_operator::Float64 = 0.2
    custom_mutation::Float64 = 0.7
end
```

次に、カスタム突然変異タイプを含めるために`sample_mutation`関数をオーバーロードします：

```julia
# 突然変異名（シンボル）のリストを定義
const MY_MUTATIONS = [
    :mutate_constant,
    :mutate_operator,
    :custom_mutation
]

# オーバーロードするために`sample_mutation`関数をインポート
import SymbolicRegression: sample_mutation
using StatsBase: StatsBase

# `sample_mutation`関数をオーバーロード
function sample_mutation(w::MyMutationWeights)
    weights = [
        w.mutate_constant,
        w.mutate_operator,
        w.custom_mutation
    ]
    weights = weights ./ sum(weights)  # 重みを1.0に正規化
    return StatsBase.sample(MY_MUTATIONS, StatsBase.Weights(weights))
end

# `Options`を定義する際に渡す：
using SymbolicRegression: Options
options = Options(mutation_weights=MyMutationWeights())
```

これにより、指定された重みに従ってカスタム突然変異を含む突然変異サンプリングプロセスをカスタマイズできます。

カスタム突然変異を突然変異プロセスに統合するには、カスタム突然変異タイプに対応する突然変異関数が定義され、シンボリック回帰フレームワークに適切に登録されていることを確認してください。カスタム突然変異タイプを処理するための`mutate!`のメソッドを定義する必要があるかもしれません。

# 参照

  * [`MutationWeights`](@ref): デフォルトの突然変異重みを定義する`AbstractMutationWeights`の具体的な実装。
  * [`sample_mutation`](@ref): 現在の突然変異重みに基づいて突然変異をサンプリングする関数。
  * [`mutate!`](@ref SymbolicRegression.MutateModule.mutate!): 式ツリーに突然変異を適用する関数。
  * [`AbstractOptions`](@ref SymbolicRegression.OptionsStruct.AbstractOptions): オプションをカスタマイズするための抽象型を拡張する方法を参照してください。
