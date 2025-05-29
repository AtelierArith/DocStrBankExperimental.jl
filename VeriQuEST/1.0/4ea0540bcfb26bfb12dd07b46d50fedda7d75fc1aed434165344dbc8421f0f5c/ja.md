```
run_verification_simulator(::MaliciousServer, ::Terse, para, malicious_angles)
```

悪意のあるサーバーのコンテキストで検証シミュレーターを実行します。シミュレーターは、色付けの定義、逆流の計算、グラフリソースの作成、ランダムラウンドの描画、検証の実行、ラウンドの検証、およびモード出力の取得を含みます。

# 引数

  * `::MaliciousServer`: この関数が悪意のあるサーバーのコンテキストで使用されることを示します。
  * `::Terse`: この関数が簡潔モードで使用されることを示します。
  * `para::Dict`: シミュレーションのためのパラメータを含む辞書。
  * `malicious_angles::Union{Float64,Vector{Float64}}`: 悪意のある行動に使用される角度。

# 例

```julia
para = Dict("input" => Dict("indices" => [1, 2, 3], "values" => [0.5, 0.5, 0.5]), "output" => [4, 5, 6], "graph" => create_graph(Client(), 3), "secret_angles" => [π/4, π/2, 3π/4], "forward_flow" => [0.1, 0.2, 0.3], "total_rounds" => 10, "computation_rounds" => 5, "state_type" => :state1)
malicious_angles = [π/4, π/2, 3π/4]
run_verification_simulator(MaliciousServer(), Terse(), para, malicious_angles)
```
