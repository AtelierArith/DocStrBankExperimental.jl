```
SpeedMappingJL(;
    σ_min = 0.0, stabilize::Bool = false, check_obj::Bool = false,
    orders::Vector{Int} = [3, 3, 2]
)
```

固定点問題を解決するための[SpeedMapping.jl](https://nicolasl-s.github.io/SpeedMapping.jl/)のラッパーです。このアルゴリズムを使用して根を見つける問題を解決することも可能です。

### キーワード引数

  * `σ_min`: `1`に設定すると、スタンバイを回避できる場合があります（[lepage2021alternating](@cite)を参照）。
  * `stabilize`: 外挿の前に安定化マッピングを実行します。`true`に設定すると、EMやMMアルゴリズムの加速などのアプリケーションでパフォーマンスが向上する可能性があります（[lepage2021alternating](@cite)を参照）。
  * `check_obj`: NaNまたはInfの値がある場合、アルゴリズムは過去の最良の反復から再起動します。
  * `orders`: ACXの交互順序を決定します。`1`から`3`の間でなければなりません（`1`は外挿なしを意味します）。推奨される2つの順序は`[3, 2]`と`[3, 3, 2]`であり、後者は非常に非線形なアプリケーションに対してより良い可能性があります（[lepage2021alternating](@cite)を参照）。

!!! note
    このアルゴリズムは`SpeedMapping.jl`がインストールされ、ロードされている場合にのみ利用可能です。

