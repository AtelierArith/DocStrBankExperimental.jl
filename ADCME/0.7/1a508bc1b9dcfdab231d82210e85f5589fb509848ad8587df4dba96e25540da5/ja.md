```
AdamOptimizer(learning_rate=1e-3;kwargs...)
```

ADAMオプティマイザを構築します。

# 例

```julia
learning_rate = 1e-3
opt = AdamOptimizer(learning_rate).minimize(loss)
sess = Session(); init(sess)
for i = 1:1000
    _, l = run(sess, [opt, loss])
    @info "イテレーション $i, 損失 = $l")
end
```

# 動的学習率

動的学習率を使用することもできます。たとえば、学習率 $l_t = \frac{1}{1+t}$ を使用したい場合、次のようになります。

```julia
learning_rate = placeholder(1.0)
opt = AdamOptimizer(learning_rate).minimize(loss)
sess = Session(); init(sess)
for i = 1:1000
    _, l = run(sess, [opt, loss], lr = 1/(1+i))
    @info "イテレーション $i, 損失 = $l")
end
```

[`GradientDescentOptimizer`](@ref)、[`AdadeltaOptimizer`](@ref) などの他のオプティマイザの使用法も似ています：`AdamOptimizer` を対応するものに置き換えるだけです。
