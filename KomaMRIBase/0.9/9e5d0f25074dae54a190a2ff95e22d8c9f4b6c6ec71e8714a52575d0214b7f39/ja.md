```
translate = Translate(dx, dy, dz)
```

Translate 構造体。線形変換を生成します。そのフィールドは、3つの軸における最終的な変位 (dx, dy, dz) です。

# 引数

  * `dx`: (`::Real`, `[m]`) x 軸の変換
  * `dy`: (`::Real`, `[m]`) y 軸の変換
  * `dz`: (`::Real`, `[m]`) z 軸の変換

# 戻り値

  * `translate`: (`::Translate`) Translate 構造体

# 例

```julia-repl
julia> translate = Translate(dx=0.01, dy=0.02, dz=0.03)
```
