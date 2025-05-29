```julia
VIDAProblem(div, f, lb, ub)

```

最適化のための `VIDAProblem` を定義します。

## 引数

  * `div`: 適合させたいダイバージェンス。これは [`VIDA.AbstractDivergence`](@ref) のインスタンスです。
  * `f`:   適合させるテンプレートのパラメトリックファミリーを定義する関数。この関数は、最初の引数として名前付きタプルを受け入れ、その名前がパラメータを定義します。
  * `lb`:  `f` の引数と一致する名前を持ち、検索したいパラメータ範囲の下限を定義する値を持つ名前付きタプル
  * `ub`: `f` の引数と一致する名前を持ち、検索したいパラメータ範囲の上限を定義する値を持つ名前付きタプル

## 例

```julia-repl
julia> f(x) = SlashedGaussianRing(x.σ, x.s)
julia> div = Renyi(img, 0.75)
julia> lb = (x = 0.1, s = 0.001)
julia> ub = (x = 10.0, s = 0.999)
julia> prob = VIDAProblem(div, f, lb, ub)
```
