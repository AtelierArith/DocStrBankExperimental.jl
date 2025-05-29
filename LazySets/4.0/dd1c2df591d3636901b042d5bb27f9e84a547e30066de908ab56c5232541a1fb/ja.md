```
rand(::Type{HPOLYGON}; [N]::Type=Float64, [dim]::Int=2,
     [rng]::AbstractRNG=GLOBAL_RNG, [seed]::Union{Int, Nothing}=nothing,
     [num_constraints]::Int=-1) where {HPOLYGON<:AbstractHPolygon}
```

制約表現でランダムポリゴンを作成します。

### 入力

  * `HPOLYGON`        – ディスパッチ用の型
  * `N`               – （オプション、デフォルト: `Float64`）数値型
  * `dim`             – （オプション、デフォルト: 2）次元
  * `rng`             – （オプション、デフォルト: `GLOBAL_RNG`）乱数生成器
  * `seed`            – （オプション、デフォルト: `nothing`）再シード用のシード
  * `num_constraints` – （オプション、デフォルト: `-1`）ポリゴンの制約の数（3以上でなければならない; 下記のコメントを参照）

### 出力

制約表現でのランダムポリゴン。

### アルゴリズム

頂点表現でランダムポリゴンを作成し、それを制約表現に変換します。 [`rand(::Type{VPolygon})`](@ref)を参照してください。平坦でないポリゴンの場合、頂点の数と制約の数は同じです。
