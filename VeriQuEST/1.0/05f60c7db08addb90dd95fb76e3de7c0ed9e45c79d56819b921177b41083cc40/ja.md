```
run_verification_simulator(server::NoisyServer, ::Terse, para)
```

`NoisyServer`上で検証シミュレーターを実行します。計算とテストラウンドのための色付けを定義し、テストラウンドのしきい値を計算し、クライアントリソースを作成し、ランダムラウンドを描画し、検証を実行し、ラウンドを検証し、モードの結果を取得します。テスト検証、計算検証、およびモードの結果を含むタプルを返します。

# 引数

  * `server::NoisyServer`: 検証シミュレーターが実行される`NoisyServer`インスタンス。
  * `::Terse`: 検証プロセスの冗長性レベル。
  * `para`: 検証プロセスのためのパラメータを含む辞書。

# 戻り値

  * `Tuple`: テスト検証（`test_verification`）、計算検証（`computation_verification`）、およびモードの結果（`mode_outcome`）を含むタプル。

# 例

```julia
server = NoisyServer(noise_model)
para = Dict(:graph => create_graph(Client(), 3), :input => Dict(:indices => [1, 2], :values => [0, 1]), :output => [3], :secret_angles => [0.5, 0.5], :forward_flow => [0.5, 0.5], :total_rounds => 10, :computation_rounds => 5, :state_type => :state1)
results = run_verification_simulator(server, Terse(), para)
```
