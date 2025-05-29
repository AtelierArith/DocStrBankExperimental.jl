```
A, B, C, T = balance_statespace{S}(A::Matrix{S}, B::Matrix{S}, C::Matrix{S}, perm::Bool=false)
sys, T = balance_statespace(sys::StateSpace, perm::Bool=false)
```

システムの行と列のノルムがほぼ等しくなるように、バランシング変換 `T` を計算します。ここで、`[T*A/T T*B; C/T 0]` です。`perm=true` の場合、`A` の状態は再配置されることが許可されます。

`sysb, T = balance_statespace(sys)` の逆は `similarity_transform(sysb, T)` で与えられます。

これは、等しく対角の可観測性および到達可能性グラミアンを持つバランスされた実現を見つけることとは異なります。詳細は [`balreal`](@ref) を参照してください。
