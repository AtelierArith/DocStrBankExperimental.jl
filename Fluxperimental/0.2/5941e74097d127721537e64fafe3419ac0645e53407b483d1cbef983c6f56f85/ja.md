```
@compact(forward::Function; name=nothing, parameters...)
```

いくつかの`parameters`をキーワードの形で指定し、（通常は`do`ブロックとして）フォワードパスのための関数を指定することでレイヤーを作成します。`@compact`は、Fluxで学習可能なローカル変数を作成する特化型の`let`ブロックのように考えることができます。宣言された変数名は`forward`関数の本体内で使用できます。

以下は線形モデルです：

```
r = @compact(w = rand(3)) do x
  w .* x
end
r([1, 1, 1])  # xは[1, 1, 1]に設定されます。
```

以下はバイアスと活性化を持つ線形モデルです：

```
d_in = 5
d_out = 7
d = @compact(W = randn(d_out, d_in), b = zeros(d_out), act = relu) do x
  y = W * x
  act.(y .+ b)
end
d(ones(5, 10)) # 出力として7×10行列。
d([1,2,3,4,5]) ≈ Dense(d.variables.W, zeros(7), relu)([1,2,3,4,5]) # 密なレイヤーに相当
```

```

最後に、シンプルなMLPがあります：

```

using Flux

n*in = 1 n*out = 1 nlayers = 3

model = @compact(   w1=Dense(n*in, 128),   w2=[Dense(128, 128) for i=1:nlayers],   w3=Dense(128, n*out),   act=relu ) do x   embed = act(w1(x))   for w in w2     embed = act(w(embed))   end   out = w3(embed)   return out end

model(randn(n_in, 32))  # 出力として1×32行列。

```

このモデルは、他の`Chain`と同様にトレーニングできます：

```

data = [([x], 2x-x^3) for x in -2:0.1f0:2] optim = Flux.setup(Adam(), model)

for epoch in 1:1000   Flux.train!((m,x,y) -> (m(x) - y)^2, model, data, optim) end ```モデルのカスタム出力を指定するには、[`NoShow`](@ref)が便利です。```
