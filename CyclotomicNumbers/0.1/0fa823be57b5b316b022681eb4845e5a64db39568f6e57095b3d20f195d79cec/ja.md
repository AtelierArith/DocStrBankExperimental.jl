`Quadratic(c::Cyc)`

は `c` が `ℚ` の二次拡張に存在するかどうかを判断します。呼び出し `q=Quadratic(c)` は、`c==(q.a + q.b root(q.root))//q.den` という形で表現可能な場合、フィールド `q.a`, `q.b`, `q.root`, `q.den` を持つ構造体 `Quadratic` を返します。そうでない場合は `nothing` を返します。

# 例

```julia-repl
julia> Quadratic(E(3,2)-2E(3))
(1-3√-3)/2

julia> Quadratic(1+E(5))

```
