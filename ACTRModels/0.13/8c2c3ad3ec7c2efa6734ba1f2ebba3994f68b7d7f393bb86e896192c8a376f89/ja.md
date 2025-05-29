```
retrieve(actr::AbstractACTR; request...)
```

取得リクエストに基づいてチャンクを取得します。デフォルトでは、現在の時間は `get_time` で計算されます。

# 引数

  * `actr::AbstractACTR`: ACT-Rオブジェクト

# キーワード

  * `request...`: 取得リクエストを表すオプションのキーワード引数、例: person=:bob

# 例

```julia
using ACTRModels 
chunks = [Chunk(country=:Germany, capitol=:Berlin),
        Chunk(country=:Australia, capitol=:Canberra)]
declarative = Declarative(memory=chunks)
parms = (noise=true, s=0.20)
actr = ACTR(;declarative, parms...)
retrieve(actr; country=:Germany)
```
