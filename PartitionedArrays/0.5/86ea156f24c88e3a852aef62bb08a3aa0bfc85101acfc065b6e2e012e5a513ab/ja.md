```
struct DebugArray{T,N}
```

[`MPIArray`](@ref) の制限をエミュレートするデータ構造ですが、標準の逐次（いわゆるシリアル）Juliaセッションで使用できます。この構造体はJulia配列インターフェースを実装しています。[`MPIArray`](@ref) と同様に、`DebugArray` に対して `setindex!` と `getindex` を使用することは無効です。これは、実際の並列実行では効率的ではないためです（通信コスト）。

# プロパティ

この構造体のフィールドはプライベートです。

# スーパタイプ階層

```
DebugArray{T,N} <: AbstractArray{T,N}
```
