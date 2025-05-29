```julia
struct FEVector{T, Tv, Ti}
```

平坦な配列ですが、関連するFESpaceの係数を持ついくつかのFEVectorBlockのサブディビジョンの追加レイヤーがあります。j番目のブロックにはgetindex(::FEVector, j)またはタグが関連付けられている場合はgetindex(::FEVector, tag)を使用してアクセスできます。完全なベクトルにはFEVector.entriesを介してアクセスできます。
