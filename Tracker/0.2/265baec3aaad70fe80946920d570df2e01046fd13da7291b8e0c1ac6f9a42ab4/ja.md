```
withgradient(f, xs...)
```

これは `f(xs...)` の値と `xs` に関する勾配を計算します。ただし、いくつかの点で `gradient` とは異なります：

  * `fmap` を使用して `xs` に再帰的に入るため、Zygote の「明示的モード」のように、Flux モデルの形状に一致する木構造の勾配を返します。この再帰は、定義されている場合、`Optimisers.trainable` によって課せられた制約に従います。
  * `Optimisers.isnumeric` を満たすオブジェクトのみがパラメータと見なされるため、特に整数の配列は無視されます。
  * トラッキングされない平坦な配列を返します。Zygote のように、強いゼロ勾配として `nothing` を使用します。
  * `gradient` で使用されるスカラーに加えて、補助出力をキャプチャすることを許可します。これを行うには、`f` がタプルまたは名前付きタプルを返す必要があります。次に、`grad = gradient(first∘f, args...)` を計算しますが、全体の `val = f(args...)` を返します：

# 例

```
julia> nt = (vec = [1.0, 2.0], mat = [4.0;;], fun = sin);

julia> withgradient(nt, 2) do x, p
         sum(abs2, x.vec) ^ p
       end
(val = 25.0, grad = ((vec = [20.0, 40.0], mat = [0.0;;], fun = nothing), nothing))

julia> using Flux

julia> model = Chain(Dense(2 => 1, tanh), Dense(1 => 1, bias=false));

julia> withgradient(model, rand(Float32, 2)) do m, x
         sum(abs2, m(x))
       end
(val = 0.035716165f0, grad = ((layers = ((weight = Float32[-0.4241869 -0.16741231], bias = Float32[-0.5529184], σ = nothing), (weight = Float32[-0.04804218;;], bias = nothing, σ = nothing)),), Float32[0.12706584, -0.08858479]))
```
