# 関数呼び出し

`pol(r, phi)`

# 説明

長さ `r` と角度 `phi` を持つ複素数を作成します。

# 変数

`r` 複素数の長さ; r は Unitful によって生成された単位を含めて利用できます。

`phi` 複素数の角度; Unitful モジュールを利用する場合、角度は単位 `°` を使用して度で指定できます。

# 例

```julia
julia> using Unitful, Unitful.DefaultSymbols, ElectricalEngineering
julia> U1 = pol(2V,pi)
-2 + 0im V
julia> U2 = pol(sqrt(2)*1V,45°)
1 + 1im V
```
