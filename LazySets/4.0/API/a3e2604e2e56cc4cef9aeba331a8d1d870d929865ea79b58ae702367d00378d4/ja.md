```
rand(T::Type{<:LazySet}; [N]::Type{<:Real}=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing
    )
```

指定されたセットタイプのランダムセットを作成します。

### 入力

  * `T`    – セットタイプ
  * `N`    – （オプション、デフォルト: `Float64`）数値タイプ
  * `dim`  – （オプション、デフォルト: 2）次元
  * `rng`  – （オプション、デフォルト: `GLOBAL_RNG`）乱数生成器
  * `seed` – （オプション、デフォルト: `nothing`）再シード用のシード

### 出力

指定されたセットタイプのランダムセット。
