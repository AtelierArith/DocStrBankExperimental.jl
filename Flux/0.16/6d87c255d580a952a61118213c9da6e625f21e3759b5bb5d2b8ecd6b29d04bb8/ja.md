```
gradient(f, args...)
```

引数 `x` ごとの `∂f/∂x` を含むタプルを返します。スカラー `x` の場合は導関数、または勾配です。勾配が定義されていない場合、`∂f/∂x` は `nothing` になります。

`f(args...)` は実数でなければなりません。配列出力については [`Zygote.jacobian`](@ref) を参照してください。

デフォルトでは、`Flux.gradient` は Zygote を呼び出します。Enzyme をロードすると、他のメソッドが利用可能になります。

値 `f(args...)` を保持するための [`withgradient`](@ref) も参照してください。

# 例

```
julia> Flux.gradient(*, 2.0, 3.0, 5.0)
(15.0, 10.0, 6.0)

julia> Flux.gradient(x -> sum(abs2,x), [7.0, 11.0, 13.0])
([14.0, 22.0, 26.0],)

julia> Flux.gradient([7, 11], 0, 1) do x, y, d
         p = size(x, d)
         sum(x.^p .+ y)
       end
([14.0, 22.0], 2.0, nothing)
```
