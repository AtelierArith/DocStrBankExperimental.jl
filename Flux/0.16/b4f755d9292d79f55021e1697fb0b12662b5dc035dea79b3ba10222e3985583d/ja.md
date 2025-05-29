```
withgradient(f, args...)
```

関数の値と[`gradient`](@ref)を名前付きタプルとして返します。

デフォルトでは、`Flux.withgradient`はZygoteを呼び出します。Enzymeをロードすると、他のメソッドが利用可能になります。

# 例

```
julia> y, ∇ = withgradient(/, 1, 2)
(val = 0.5, grad = (0.5, -0.25))

julia> ∇ == gradient(/, 1, 2)
true
```

`gradient`で使用されるスカラーに加えて、補助出力をキャプチャすることができます。これを行うには、`f`がタプルまたは名前付きタプルを返す必要があります。次に、`grad = gradient(first∘f, args...)`を計算しますが、全体の`val = f(args...)`を返します：

```jldoctest; setup=:(using Zygote)
julia> withgradient([1,2,4]) do x
          z = 1 ./ x
          sum(z), z  # ここでzは補助出力です
       end
(val = (1.75, [1.0, 0.5, 0.25]), grad = ([-1.0, -0.25, -0.0625],))

julia> withgradient(3.0, 4.0) do x, y
          (div = x/y, mul = x*y)
       end
(val = (div = 0.75, mul = 12.0), grad = (0.25, -0.1875))
```
