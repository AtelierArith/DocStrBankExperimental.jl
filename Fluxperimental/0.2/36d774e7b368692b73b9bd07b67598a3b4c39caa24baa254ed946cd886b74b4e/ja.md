```
shinkansen!(loss, model, data...; state, epochs=1, [batchsize, keywords...])
```

これは`train!`の再設計です：

  * 損失関数は残りの引数を受け入れなければなりません：`loss(model, data...)`
  * `setup`からのオプティマイザの状態はキーワード`state`に渡されなければなりません。

デフォルトでは、`gradient(loss, model, data...)`をそのまま呼び出します。引数の順序は同じです。`epochs = 100`を指定すると、これを100回実行します。

しかし、`batchsize = 32`を指定すると、最初に`DataLoader(data...; batchsize)`を作成し、それを使用して`gradient`に供給する小さな配列を生成します。他のすべてのキーワードは`DataLoader`に渡されます。例えば、バッチをシャッフルするために使用されます。

すべての呼び出しからの損失を返します。

# 例

```
X = repeat(hcat(digits.(0:3, base=2, pad=2)...), 1, 32)
Y = Flux.onehotbatch(xor.(eachrow(X)...), 0:1)

model = Chain(Dense(2 => 3, sigmoid), BatchNorm(3), Dense(3 => 2))
state = Flux.setup(Adam(0.1, (0.7, 0.95)), model)
# state = Optimisers.setup(Optimisers.Adam(0.1, (0.7, 0.95)), model)  # とりあえず

shinkansen!(model, X, Y; state, epochs=100, batchsize=16, shuffle=true) do m, x, y
    Flux.logitcrossentropy(m(x), y)
end

all((softmax(model(X)) .> 0.5) .== Y)
```
