```julia
expand_derivatives(O; ...)
expand_derivatives(O, simplify; throw_no_derivative)

```

シンボリック表現 `O` 内の導関数を展開します。

この関数はシンボリック表現を再帰的に走査し、出会った導関数を展開するために連鎖律やその他の導関数のルールを適用します。

# 引数

  * `O::Symbolic`: 展開するシンボリック表現。
  * `simplify::Bool=false`: [`SymbolicUtils.simplify`](@ref) を使用して結果の表現を簡略化するかどうか。

# キーワード引数

  * `throw_no_derivative=false`: 未知の導関数を持つ関数に出会った場合に例外を投げるかどうか。

# 例

```jldoctest
julia> @variables x y z k;

julia> f = k*(abs(x-y)/y-z)^2
k*((abs(x - y) / y - z)^2)

julia> Dx = Differential(x) # x に関して微分
(::Differential) (generic function with 2 methods)

julia> dfx = expand_derivatives(Dx(f))
(k*((2abs(x - y)) / y - 2z)*ifelse(signbit(x - y), -1, 1)) / y
```
