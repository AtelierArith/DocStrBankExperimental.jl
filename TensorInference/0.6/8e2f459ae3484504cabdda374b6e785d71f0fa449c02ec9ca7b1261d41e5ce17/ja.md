```julia
struct MMAPModel{LT, AT<:AbstractArray}
```

クエリ変数 Xₘ ⊆ X に対する最も可能性の高い割り当てを計算し、残りの変数 Xₛ = X \ Xₘ を周辺化します。

$$
{\rm MMAP}(X_i|E=e) = \arg \max_{X_M} \sum_{X_S} \prod_{F} f(x_M, x_S, e)
$$

### フィールド

  * `vars` はテンソルネットワーク内のクエリ変数です。
  * `code` はトロピカルテンソルネットワークの収縮パターンです。
  * `tensors` はテンソルネットワークに供給されるテンソルです。
  * `clusters` はクラスタであり、このクラスタの各要素は特定の変数を周辺化するための [`TensorNetworkModel`](@ref) インスタンスです。
  * `evidence` は特定の値に固定された自由度を指定するための辞書であり、クエリ変数と重複してはいけません。
