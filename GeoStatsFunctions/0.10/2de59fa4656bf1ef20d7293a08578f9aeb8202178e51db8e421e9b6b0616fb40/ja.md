```
funplot!(fig, f; [options])
```

関数 `f` のプロットで図 `fig` が更新される [`funplot`(@ref)] の変異バージョンです。

## 例

```julia
# ガウス変動関数で図を初期化
fig = funplot(GaussianVariogram())

# 図に球状変動関数を追加
funplot!(fig, SphericalVariogram())
```

`options` のための [`funplot`](@ref) のドキュメントを参照してください。
