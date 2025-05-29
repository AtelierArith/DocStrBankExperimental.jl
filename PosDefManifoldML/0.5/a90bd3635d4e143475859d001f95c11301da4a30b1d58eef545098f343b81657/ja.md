```julia
function dim(pipeline::Pipeline)
```

フィッティングされた [`Recenter`](@ref) 前処理器が `pipeline` に含まれている場合は、その次元を返し、そうでない場合は `nothing` を返します。これはパイプラインを適応させるために使用されます - ENLR 機械学習モデルの例については [`fit!`](@ref) 関数のドキュメントを参照してください。

**例**

```julia
using PosDefManifoldML, PosDefManifold

pipeline = @→ Recenter(; eVar=0.9) → Shrink()
dim(pipeline) # フィッティングされていないため、falseを返す

P = randP(10, 5)
p = fit!(P, pipeline)
dim(p) # 整数 ≤ 10 を返す
```

**パッケージを学ぶ**: [`@pipeline`](@ref) をチェックしてください
