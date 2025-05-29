```julia
get_example_network_params(name)

```

名前付きの例のニューラルネットワークを[`NeuralNet`](@ref)オブジェクトとして利用可能にします。

# 引数

  * `name::String`: 例のニューラルネットワークの名前。オプション:

      * `'MNIST.n1'`:

          * アーキテクチャ: 40および20ユニットの2つの全結合層。
          * トレーニング: ロバスト性を高める試みなしに定期的にトレーニングされた。
      * `'MNIST.WK17a_linf0.1_authors'`.

          * アーキテクチャ: それぞれ16および32フィルタを持つ2つの畳み込み層（ストライド長2）、両層でサイズ4 × 4、次に100ユニットの全結合層。
          * トレーニング: [Provable defenses against adversarial examples via the convex outer adversarial polytope](https://arxiv.org/abs/1711.00851)の方法を通じて、$l_\infty$ノルムが最大0.1の攻撃に対してロバストになるようにトレーニングされたネットワーク。論文で結果が報告されているMNISTネットワークです。
      * `'MNIST.RSL18a_linf0.1_authors'`.

          * アーキテクチャ: 500ユニットの1つの全結合層。
          * トレーニング: [Certified Defenses against Adversarial Examples ](https://arxiv.org/abs/1801.09344)の方法を通じて、$l_\infty$ノルムが最大0.1の攻撃に対してロバストになるようにトレーニングされたネットワーク。論文で結果が報告されているMNISTネットワークです。
