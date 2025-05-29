```
load_logger_from_config(config::Dict)::TeeLogger
```

`Dict`から`TeeLogger`、すなわちロガーのコレクションを作成します。

### 注意

  * `TeeLogger`構造体は、同じログメッセージを`TeeLogger`に含まれるすべてのロガーに一度に送信することを可能にします。
  * 設定`Dict`は、`"logging"`フィールドを必要とします。詳細については例を参照してください。

### 例

```julia
config = Dict(
    ...,
    "logging" => [
        # logger_type => logger_config_dict,
        "SeqLogger" => Dict(...),
        ...
    ],
    ...
)
```

### 戻り値

`config`で定義された`TeeLogger`
