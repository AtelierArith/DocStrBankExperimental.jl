```
Prometheus.@inprogress collector expr
```

`expr`の同時進行中の評価の数を追跡します。組み込みコレクタの中で、これは[`Gauge`](@ref)にのみ適用可能です – ガウジの値は、セクションに入るときに1増加し、セクションを出るときに1減少します。

式`expr`は、単一の式（例えば関数呼び出し）またはコードブロック（`begin`、`let`など）であることができます。例えば：

```julia
Prometheus.@inprogress collector <expr>

Prometheus.@inprogress collector begin
    <expr>
end
```

マクロを関数の*定義*に適用することも可能です。すなわち：

```julia
Prometheus.@inprogress collector function track_this(args...)
    # 関数本体
end
```

これにより、同時進行中の呼び出しの数を追跡できます（すべての呼び出し元をカバーします）。
