```
SphericalDirections{N<:AbstractFloat, VN<:AbstractVector{N}} <: AbstractDirections{N, VN}
```

球面方向の表現。

### フィールド

  * `Nθ`    – 方位角の分割の長さ
  * `Nφ`    – 極角の分割の長さ
  * `stack` – 計算された方向のリスト

### ノート

`SphericalDirections` コンストラクタは、$ℝ^3$ の単位球のサンプルを提供し、これは方位角 $θ ∈ Dθ := [0, π]$ と極角 $φ ∈ Dφ := [0, 2π]$ によってパラメータ化されます。詳細については、[球面座標系](https://en.wikipedia.org/wiki/Spherical_coordinate_system)に関するWikipediaのエントリを参照してください。

整数引数 $Nθ$ と $Nφ$ は、それぞれ $Dθ$ と $Dφ$ のドメインに沿ってどれだけのサンプルが取られるかを定義します。各方向のデカルト成分は次のように得られます。

$$
[sin(θᵢ)*cos(φᵢ), sin(θᵢ)*sin(φᵢ), cos(θᵢ)].
$$

北極と南極は別々に扱われるため、これらの点は一度以上考慮されることはありません。

### 例

テンプレートは異なる方法で構築できます。整数を1つだけ渡すと、同じ値が $θ$ と $φ$ の両方を離散化するために使用されます：

```jldoctest spherical_directions; filter = r"1232[0-9]*e-17.*2246[0-9]*e-16.*1232[0-9]*e-17"
julia> sd = SphericalDirections(3);

julia> sd.Nθ, sd.Nφ
(3, 3)

julia> length(sd)
4
```

2つの整数を渡して、$θ$ と $φ$ の離散化を別々に制御します：

```jldoctest spherical_directions
julia> sd = SphericalDirections(4, 5);

julia> length(sd)
10

julia> sd = SphericalDirections(4, 8);

julia> length(sd)
16
```
