```
PolarDirections{N<:AbstractFloat, VN<:AbstractVector{N}} <: AbstractDirections{N, VN}
```

極方向の表現。

### フィールド

  * `Nφ`    – 極角の分割の長さ
  * `stack` – 計算された方向のリスト

### ノート

`PolarDirections` コンストラクタは、極角 $φ ∈ Dφ := [0, 2π]$ によってパラメータ化された $ℝ^2$ の単位球のサンプルを計算します。詳細については、[極座標系](https://en.wikipedia.org/wiki/Polar_coordinate_system) に関するウィキペディアの項目を参照してください。結果として得られた方向は `stack` に格納されます。

整数引数 $Nφ$ は、$Dφ$ のサンプル数を定義します。各方向のデカルト成分は次のように得られます。

$$
[cos(φᵢ), sin(φᵢ)].
$$

### 例

引数として渡された整数は、$φ$ を離散化するために使用されます：

```jldoctest; filter = r"2246[0-9]*e-16"
julia> pd = PolarDirections(2);

julia> pd.stack
2-element Vector{Vector{Float64}}:
 [1.0, 0.0]
 [-1.0, 1.2246467991473532e-16]

julia> length(pd)
2
```
