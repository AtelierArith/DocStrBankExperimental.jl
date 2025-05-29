```
Prometheus.@time collector expr
```

`expr`の評価にかかる時間を計測し、経過時間を秒単位で`collector`に送信します。具体的なアクションは、コレクタのタイプによって異なります：

  * `collector :: Gauge`: ゲージの値を経過時間に設定します（[`Prometheus.set`](@ref)）
  * `collector :: Histogram`および`collector :: Summary`: 経過時間を観測値として追加します（[`Prometheus.observe`](@ref)）

計測する式`expr`は、単一の式（例えば関数呼び出し）またはコードブロック（`begin`、`let`など）であることができます。例えば：

```julia
Prometheus.@time collector <expr>

Prometheus.@time collector begin
    <expr>
end
```

マクロを関数の*定義*に適用することも可能です。つまり：

```julia
Prometheus.@time collector function time_this(args...)
    # 関数本体
end
```

これにより、この関数へのすべての呼び出しの時間を計測できます（すべての呼び出し元をカバーします）。
