```
ITensor([ElT::Type, ]A::AbstractArray, inds)
ITensor([ElT::Type, ]A::AbstractArray, inds::Index...)

itensor([ElT::Type, ]A::AbstractArray, inds)
itensor([ElT::Type, ]A::AbstractArray, inds::Index...)
```

AbstractArray `A` とインデックス `inds` から ITensor を構築します。ITensor は可能であれば AbstractArray データのビューになります（異なる要素型への変換が必要ない場合）。

指定された場合、ITensor は要素型 `ElT` を持ちます。

`A` の要素型が `Int` または `Complex{Int}` で、希望する要素型が指定されていない場合、自動的に `Float64` または `Complex{Float64}` に変換されます。要素型を整数のままにしたい場合は、明示的に指定してください。例えば、次のようにします：

```julia
i = Index(2, "i")
A = [0 1; 1 0]
T = ITensor(eltype(A), A, i', dag(i))
```

# 例

```julia
i = Index(2,"index_i")
j = Index(2,"index_j")

M = [1. 2;
     3 4]
T = ITensor(M, i, j)
T[i => 1, j => 1] = 3.3
M[1, 1] == 3.3
T[i => 1, j => 1] == 3.3
```

!!! warning
    将来のバージョンでは、`Int`/`Complex{Int}` 入力を浮動小数点バージョンに自動的に変換しない可能性があります（`Int`/`Complex{Int}` を使用したテンソル操作が浮動小数点操作と同じくらい速くなると、特定の要素型に依存しない方が良いです）。余分な変換（したがって、アロケーション）を避けるためには、浮動小数点要素型を希望する場合は、`itensor([0. 1; 1 0], i', dag(i))` で直接構築するのがベストプラクティスです。この変換はパフォーマンスの最適化として行われます。なぜなら、しばしばテンソルは BLAS/LAPACK に渡され、これらのライブラリと互換性のある浮動小数点型に変換する必要があるからです。しかし、Julia の将来のプロジェクトでは、より一般的な要素型で効率的な操作が可能になるかもしれません（例えば、https://github.com/JuliaLinearAlgebra/Octavian.jl を参照してください）。

