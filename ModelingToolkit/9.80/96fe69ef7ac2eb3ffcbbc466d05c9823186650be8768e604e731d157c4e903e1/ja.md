```julia
generate_custom_function(sys::AbstractSystem, exprs, dvs = unknowns(sys),
                         ps = parameters(sys); kwargs...)
```

`exprs`を評価する関数を生成します。`exprs`は、`sys`内の記号変数を含む記号式または記号式の配列です。記号変数は、`dvs`および`ps`を使用して部分集合化できます。すべての`kwargs`は内部の[`build_function`](@ref)呼び出しに渡されます。返される関数は、時間依存システムの場合は`f(u, p, t)`または`f(du, u, p, t)`として呼び出すことができ、時間非依存システムの場合は`f(u, p)`または`f(du, u, p)`として呼び出すことができます。`split=true`（デフォルト）を[`complete`](@ref)、[`structural_simplify`](@ref)または[`@mtkbuild`](@ref)に渡した場合、`p`は`MTKParameters`オブジェクトであることが期待されます。
