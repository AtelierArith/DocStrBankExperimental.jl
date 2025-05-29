```
barycentric_weights(x::AbstractVector{TF}) where {TF<:AbstractFloat}
barycentric_weights(x::AbstractRange{TF}) where {TF<:AbstractFloat}
barycentric_weights([TF=Float64], order::Integer) where {TF<:AbstractFloat}
```

補間ノードのための正規化されたバリセントリック重みを計算します。これらの重みはバリセントリックラグランジュ補間に使用されます。チェビシェフ-ガウスノードまたはチェビシェフ-ロバットノードの場合、[cheb*gauss*barycentric_weights](@ref Einstein.ChebyshevSuite.cheb_gauss_barycentric_weights)および[cheb*lobatto*barycentric_weights](@ref Einstein.ChebyshevSuite.cheb_lobatto_barycentric_weights)がより効率的な実装です。

# 引数

  * `x::AbstractVector{TF}`: 異なる補間ノードのベクトル。等間隔のノードの場合は、範囲を使用することをお勧めします `x = x_min:dx:x_max`
  * `order::Integer`: 補間の次数 (order = length(x) - 1)

# 戻り値

  * `Vector{TF}`: 無限ノルムが1になるようにスケーリングされたバリセントリック重み

# 詳細

ノード $x_j$ に対するバリセントリック重み $w_j$ は次のように計算されます：

$$
w_j = \frac{1}{\prod_{k \neq j} (x_j - x_k)}
$$

等間隔のノードの場合、二項係数に基づいたより効率的な式が使用されます。

# 例

```julia
# 任意のノードの場合
x = [0.0, 1.0, 2.0]
w = barycentric_weights(x)

# 等間隔のノードの場合
w = barycentric_weights(2)  # 3ノード: 0, 1, 2

# または
x = 0.0:0.1:1.0
w = barycentric_weights(x)
```

# 注意事項

  * 重みは数値的安定性のために単位無限ノルムになるようにスケーリングされています
  * 入力点が異ならない場合はNaNの重みを返します
  * アンダーフロー/オーバーフローを防ぐためにlog-sum-expトリックが使用されています
  * 等間隔のノードの場合、二項係数に基づいたより効率的なアルゴリズムが使用されます

# 参考文献

  * [Berrut2004](@citet*)
  * [chebfun/baryWeights.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/baryWeights.m)

```
