```
AutoTaylorDiff{order}
```

自動微分のために [TaylorDiff.jl](https://github.com/JuliaDiff/TaylorDiff.jl) バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl) によって定義されています。

# コンストラクタ

```
AutoTaylorDiff(; order = 1)
```

# 型パラメータ

  * `order`: テイラー方式の自動微分の次数
