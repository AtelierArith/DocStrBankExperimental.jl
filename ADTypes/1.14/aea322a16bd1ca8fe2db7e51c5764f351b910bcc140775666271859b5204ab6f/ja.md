```
AutoTapir
```

!!! danger
    `AutoTapir`はパッケージ名の変更に伴い非推奨です。代わりに[`AutoMooncake`](@ref)を使用してください。


自動微分のために[Tapir.jl](https://github.com/compintell/Tapir.jl)バックエンドを選択するために使用される構造体。

[ADTypes.jl](https://github.com/SciML/ADTypes.jl)によって定義されています。

# コンストラクタ

```
AutoTapir(; safe_mode=true)
```

# フィールド

  * `safe_mode::Bool`: エラーを早期にキャッチするために追加のチェックを実行するかどうか。
