```
constrained_dimensions(HS::HybridSystem)::Dict{Int,Vector{Int}}
```

各位置について、不変条件または出発遷移のガードで制約されているすべての次元を計算します。

### 入力

  * `HS`  – ハイブリッドシステム

### 出力

各位置 $ℓ$ のインデックスを、$ℓ$ で制約されている次元インデックスにマッピングする辞書 (`::Dict{Int,Vector{Int}}`)。
