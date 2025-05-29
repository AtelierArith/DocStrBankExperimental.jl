```
integrate(f::Function,nodes::AbstractVector{<:Real},weights::AbstractVector{<:Real})
integrate(f::Function,q::AbstractQuad)
integrate(f::Function,opq::AbstractOrthoPoly)
```

関数 `f` を `nodes` と `weights` で指定された数値積分ルールを使用して積分します。例えば、$\int_0^1 6x^5 = 1$ は以下のように解くことができます：

```@repl
julia> opq = Uniform01OrthoPoly(3) # デフォルトで数値積分ルールが追加されます

julia> integrate(x -> 6x^5, opq)
0.9999999999999993
```

!!! note



  * 関数 $f$ はスカラーを返すと仮定されています。
  * 積分区間は `nodes` に「隠されています」。
