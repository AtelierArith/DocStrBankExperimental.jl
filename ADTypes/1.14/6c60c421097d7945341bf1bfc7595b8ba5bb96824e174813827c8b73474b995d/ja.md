```
AutoMooncake
```

自動微分のために [Mooncake.jl](https://github.com/compintell/Mooncake.jl) バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl) によって定義されています。

# コンストラクタ

```
AutoMooncake(; config)
```

# フィールド

  * `config`: `nothing` または `Mooncake.Config` のインスタンス – 詳細については `Mooncake.Config` のドキュメントを参照してください。 `AutoMooncake(; config=nothing)` は `AutoMooncake(; config=Mooncake.Config())` と同等であり、すなわちデフォルトの構成です。
