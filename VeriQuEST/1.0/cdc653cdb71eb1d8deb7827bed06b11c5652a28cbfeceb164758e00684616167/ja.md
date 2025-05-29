```
run_verification_simulator(server::NoisyServer, ::Verbose, para)
```

`NoisyServer`上で詳細な出力を伴う検証シミュレーターを実行します。計算とテストラウンドの色付けを定義し、テストラウンドの閾値を計算し、クライアントリソースを作成し、ランダムラウンドを描画し、検証を実行し、簡潔および詳細モードの両方でラウンドを検証し、モードの結果を取得します。テスト検証、計算検証、詳細テスト検証、詳細計算検証、およびモードの結果を含むタプルを返します。

# 引数

  * `server::NoisyServer`: 検証シミュレーターが実行される`NoisyServer`インスタンス。
  * `::Verbose`: 検証プロセスの詳細レベル。
  * `para`: 検証プロセスのためのパラメータを含む辞書。

# 戻り値

  * `Tuple`: テスト検証（`test_verification`）、詳細テスト検証（`test_verification_verb`）、計算検証（`computation_verification`）、詳細計算検証（`computation_verification_verb`）、およびモードの結果（`mode_outcome`）を含むタプル。

# 例

```julia
server = NoisyServer(noise_model)
para = Dict(:graph => create_graph(Client(), 3), :input => Dict(:indices => [1, 2], :values => [0, 1]), :output => [3], :secret_angles => [0.5, 0.5], :forward_flow => [0.5, 0.5], :total_rounds => 10, :computation_rounds => 5, :state_type => :state1)
results = run_verification_simulator(server, Verbose(), para)
```
