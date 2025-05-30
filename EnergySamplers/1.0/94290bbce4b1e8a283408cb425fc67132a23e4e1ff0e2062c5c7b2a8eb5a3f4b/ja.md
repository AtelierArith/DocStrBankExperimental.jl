```
PMC(
    sampler::AbstractSampler,
    model,
    rule::AbstractSamplingRule;
    ntransitions::Int = 100,
    niter::Int = 100,
    kwargs...,
)
```

サンプラーとモデルを使用して持続的マルコフ連鎖（PMC）を実行します。持続的マルコフ連鎖は、例えば、持続的コントラスト収束（[Tieleman (2008)](https://www.cs.toronto.edu/~tijmen/pcd/pcd.pdf)）のために使用されます。これはコントラストダイバージェンス（CD）アルゴリズムの変種です。主な違いは、PCDが勾配の負のフェーズを推定するために持続的な連鎖を使用することです。これは、イテレーション間でマルコフ連鎖の状態を保持することによって行われます。

私たちの文脈では、サンプラーは持続的な連鎖であり、モデルは教師ありモデルです。サンプラーはモデルの学習した分布からサンプルを生成します。

# 注意

この関数はトレーニングを行いません。モデルからサンプルを生成するだけです。言い換えれば、コントラストダイバージェンスはありません。ジョイントエネルギーモデルのトレーニングについては、[JointEnergyModels.jl](https://github.com/JuliaTrustworthyAI/JointEnergyModels.jl)を参照してください。

# 引数

  * `sampler::AbstractSampler`: 使用するサンプラー。
  * `model`: サンプリングするモデル。
  * `rule::AbstractSamplingRule`: 使用するサンプリングルール。
  * `ntransitions::Int=100`: 実行する遷移の数。
  * `niter::Int=100`: 実行するイテレーションの数。
  * `kwargs...`: 追加のキーワード引数。

# 戻り値

  * `sampler.buffer`: サンプラーによって生成されたサンプルを含むバッファ。
