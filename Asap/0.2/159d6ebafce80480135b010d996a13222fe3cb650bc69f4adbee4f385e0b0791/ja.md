```
Node(position::Vector{Float64}, dofs::Vector{Bool}, id::Symbol = nothing)
```

与えられた位置と拘束条件で6自由度ノードをインスタンス化します。オプションのシンボル識別子 `id`。

# 例

```julia-repl
julia> Node([4.3, 2.2, 10.4], [true, true, false, true, false, false])
Node([4.3, 2.2, 10.4], Bool[1, 1, 0, 1, 0, 0], #undef, #undef, #undef, nothing)
```

---

```
Node(position::Vector{Float64}, fixity::Symbol, id::Symbol = nothing)
```

与えられた位置と一般的な境界タイプで6自由度ノードをインスタンス化します。オプションのシンボル識別子 `id`。

利用可能な境界条件：

  * :free
  * :fixed
  * :pinned
  * :(x/y/z)free
  * :(x/y/z)fixed

# 例

```julia-repl
julia> Node([4.3, 2.2, 10.4], :zfixed)
Node([4.3, 2.2, 10.4], Bool[1, 1, 0, 1, 1, 1], #undef, #undef, #undef, nothing)

```
