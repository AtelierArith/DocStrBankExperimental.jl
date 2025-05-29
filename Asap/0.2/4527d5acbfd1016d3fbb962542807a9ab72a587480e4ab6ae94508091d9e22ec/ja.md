```
TrussNode(position::Vector{Float64}, dofs::Vector{Bool}, id::Symbol = nothing)
```

指定された位置と拘束条件を持つ3自由度ノードをインスタンス化します。オプションのシンボル識別子 `id`。

# 例

```julia-repl
julia> TrussNode([1., 1., 56.], [false, true, true])
TrussNode([1.0, 1.0, 56.0], Bool[0, 1, 1], #undef, [0.0, 0.0, 0.0, 0.0, 0.0, 0.0], [0.0, 0.0, 0.0, 0.0, 0.0, 0.0], nothing)
```

---

```
TrussNode(position::Vector{Float64}, fixity::Symbol, id::Symbol = nothing)
```

指定された位置と共通の境界タイプを持つ3自由度ノードをインスタンス化します。オプションのシンボル識別子 `id`。

利用可能な境界条件：

  * :free
  * :pinned
  * :(x/y/z)free
  * :(x/y/z)fixed

# 例

```julia-repl
julia> TrussNode([1., 1., 56.], :pinned)
TrussNode([1.0, 1.0, 56.0], Bool[0, 0, 0], #undef, [0.0, 0.0, 0.0], [0.0, 0.0, 0.0], nothing)

```
