```
eachobs(data; kws...)
```

`data`に対するイテレータを返します。

[`DataLoader`](@ref)と同じ引数をサポートします。ここでの`batchsize`のデフォルトは`-1`ですが、`DataLoader`では`1`です。

# 例

```julia
X = rand(4,100)

for x in eachobs(X)
    # ループは100回実行されます
    @assert typeof(x) <: Vector{Float64}
    @assert size(x) == (4,)
end

# ミニバッチの反復
for x in eachobs(X, batchsize=10)
    # ループは10回実行されます
    @assert typeof(x) <: Matrix{Float64}
    @assert size(x) == (4,10)
end

# タプル、名前付きタプル、辞書のサポート
for (x, y) in eachobs((X, Y))
    # ...
end
```
