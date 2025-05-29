```
update!(o::Optimizer{<:BFGSOptimizer}, C, B)
```

BFGSオプティマイザを使用して更新を行います。

`C`はキャッシュで、`B`は勾配情報を含んでいます（一般的には[`global_rep`](@ref)の出力です）。

まず、*最終速度*を次のように計算します。

```julia
vecS = -o.method.η * C.H * vec(B)
```

次に、`H`を更新します。

```julia
C.H .= (𝕀 - ρ * SY) * C.H * (𝕀 - ρ * SY') + ρ * vecS * vecS'
```

ここで、`SY`は`vecS * Y'`で、`𝕀`は単位行列です。

# 実装

安定性のために、`ρ`を計算するために`δ`を使用します。

```julia
ρ = 1. / (vecS' * Y + o.method.δ)
```

これは[`AdamOptimizer`](@ref)に似ています。

# 拡張ヘルプ

もし[`Manifold`](@ref)上に重みがある場合、更新は少し難しくなります。この場合、[`vec`](@ref)操作は対応する*グローバル接空間*に一般化する必要があります。
