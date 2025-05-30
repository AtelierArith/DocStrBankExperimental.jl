```
Xoshiro(seed)
Xoshiro()
```

Xoshiro256++は、David BlackmanとSebastiano Vignaによって「Scrambled Linear Pseudorandom Number Generators」で説明された高速擬似乱数生成器です。参照実装はhttp://prng.di.unimi.itで入手可能です。

高速度に加えて、Xoshiroは小さなメモリフットプリントを持ち、多くの異なる乱数状態を長時間保持する必要があるアプリケーションに適しています。

JuliaのXoshiro実装にはバルク生成モードがあり、親から新しい仮想PRNGをシードし、SIMDを使用して並列に生成します（つまり、バルクストリームは複数のインタリーブされたxoshiroインスタンスで構成されます）。仮想PRNGは、バルクリクエストが処理されると破棄され（ヒープアロケーションを引き起こすことはありません）。

# 例

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
