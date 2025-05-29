```
random_magnetic_field_layer(ξ::Vector{Index{Int64}}, p::Vector{Float64})
```

z軸に沿ったランダムな磁場を表すランダムRzゲートの層を構築します。

各キュービットiに対して、回転角が[0, 2 pi p*i)から一様に引かれたランダムな回転Rzが適用されます。これにより、各サイトでの平均回転角はpi p*iになります。

# 引数

  * `ξ::Vector{Index{Int64}}`: キュービットサイトに対応するITensorインデックスのベクター。
  * `p::Vector{Float64}`: 回転角のスケールを設定するパラメータのベクター（キュービットごとに1つ）。

# 戻り値

各キュービットに適用されるランダムRzゲートを表すITensorのベクター。

# 例

```julia
circuit = random_magnetic_field_layer(siteinds("Qubit", 5), 0.1 * ones(5))
```
