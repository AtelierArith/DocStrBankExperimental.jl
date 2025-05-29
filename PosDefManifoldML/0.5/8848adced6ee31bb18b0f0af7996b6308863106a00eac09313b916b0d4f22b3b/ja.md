```julia
function includes(pipeline, conditioner)
```

与えられた [`Pipeline`](@ref) が `conditioner` と同じタイプのコンディショナーを含む場合は true を返します。

提供された `conditioner` は、タイプまたはコンディショナーのインスタンスである可能性があります。

**参照**: [`pickfirst`](@ref), [`@pipeline`](@ref)

**例**

```julia
using PosDefManifoldML

pipeline= @→ Recenter() → Shrink()

includes(pipeline, Shrink) # true

includes(pipeline, Shrink()) # true

# 同じタイプですが、異なるインスタンス
includes(pipeline, Shrink(Fisher; radius=0.1)) # true

includes(pipeline, Compress) # false
```

**パッケージを学ぶ**: [`saveas`](@ref) をチェックしてください
