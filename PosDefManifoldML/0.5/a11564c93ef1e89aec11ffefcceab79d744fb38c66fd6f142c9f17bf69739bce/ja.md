```julia
function pickfirst(pipeline, conditioner)
```

`pipeline`の中で`conditioner`と同じ型の最初の`conditioner`のコピーを返します。該当する`conditioner`が見つからない場合は`nothing`を返します。返されるのはコピーであり、パイプライン内の`conditioner`そのものではありません。

提供された`conditioner`は型または`conditioner`のインスタンスである可能性があります。返される要素は常にインスタンスであり、パイプラインはインスタンスのみを保持します。

**参照**: [`includes`](@ref)

**例**

```julia
using PosDefManifoldML

pipeline = @→ Recenter() Shrink()
S = pickfirst(pipeline, Shrink) 
S isa Conditioner # true
S isa Shrink # true

# conditionerのパラメータを取得
pickfirst(pipeline, Shrink).radius

```
