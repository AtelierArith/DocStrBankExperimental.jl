```
AutoFiniteDifferences{T}
```

自動微分のために[FiniteDifferences.jl](https://github.com/JuliaDiff/FiniteDifferences.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoFiniteDifferences(; fdm)
```

# フィールド

  * `fdm::T`: [`FiniteDifferenceMethod`](https://juliadiff.org/FiniteDifferences.jl/stable/pages/api/#FiniteDifferences.FiniteDifferenceMethod)
