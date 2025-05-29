```
CustomDirections{N, VN<:AbstractVector{N}} <: AbstractDirections{N, VN}
```

ユーザー定義の方向ベクトル。

### フィールド

  * `directions`          – 方向ベクトルのリスト
  * `n`                   – （オプション; デフォルト: `directions`から計算）次元
  * `check_boundedness`   – （オプション; デフォルト: `true`）有界性をチェックするフラグ
  * `check_normalization` – （オプション; デフォルト: `true`）すべての方向が正規化されているかどうかをチェックするフラグ

### 注意事項

この構造体は、ユーザー定義の方向のリストのラッパーです。方向のリスト、その次元、および（ブール値の）有界性と正規化のプロパティのキャッシュフィールドがあります。後者は、構築時にデフォルトでチェックされます。

有界性をチェックするために、各方向 $d$ に対して制約 $d·x <= 1$ を持つ多面体を構築し、この集合が有界であるかどうかをチェックします。（境界 $1$ は任意であり、この集合が空である可能性があることに注意してください。ただし、これは有界性を意味します。）

次元は自動的に決定されますが、空のベクトルが渡された場合は（その場合、オプションの引数 `n` を指定する必要があります）。

### 例

次元2のボックス方向を持つテンプレートを作成します：

```jldoctest
julia> dirs = CustomDirections([[1.0, 0.0], [-1.0, 0.0], [0.0, 1.0], [0.0, -1.0]]);

julia> dirs.directions
4-element Vector{Vector{Float64}}:
 [1.0, 0.0]
 [-1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]

julia> LazySets.Approximations.isbounding(dirs)
true

julia> LazySets.Approximations.isnormalized(dirs)
true
```
