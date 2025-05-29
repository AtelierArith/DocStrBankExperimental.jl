```
cache_info(lru::LRU) -> CacheInfo
```

`CacheInfo`オブジェクトを返し、キャッシュのヒット、ミス、現在のサイズ、および最大サイズに関する情報のスナップショットを保持します。関数が呼び出された時点での情報です。値にプログラム的にアクセスするには、プロパティアクセスを使用します。例: `info.hits`。

`get!`と`get`のみがヒットとミスに寄与し、`empty!`はヒットとミスのカウントを0にリセットします。

## 例

```jldoctest
lru = LRU{Int, Float64}(maxsize=10)

get!(lru, 1, 1.0) # ミス

get!(lru, 1, 1.0) # ヒット

get(lru, 2, 2) # ミス

get(lru, 2, 2) # ミス

info = cache_info(lru)

# 出力

CacheInfo(; hits=1, misses=3, currentsize=1, maxsize=10)
```
