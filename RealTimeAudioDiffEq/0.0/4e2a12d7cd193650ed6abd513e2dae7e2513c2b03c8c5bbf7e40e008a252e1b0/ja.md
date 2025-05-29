```
DESource(f, u0::Vector{Float64}, p::Vector{Float64};
	alg = Tsit5(), channel_map::Vector{Int} = [1, 1])::DESource
```

ODEFunctionからDESourceを作成します。

# 引数

  * `f::ODEFunction`: ODE関数。形式は `f(du, u, p, t)`（インプレース）である必要があります。
  * `u0`: 初期値の配列。
  * `p`: パラメータの配列。

# キーワード引数

  * `alg::DEAlgorithm = Tsit5()`: ソルバーに渡されるアルゴリズム。
  * `channel_map::Vector{Int} = [1, 1]`: チャンネルマップは、システムの変数がオーディオデバイスの出力チャンネルにどのようにマッピングされるべきかを示します。配列内の位置はチャンネル番号を表し、値は変数を表します。
