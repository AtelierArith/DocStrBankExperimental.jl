```
check_gn(url::AbstractString)
```

GeneNetworkサーバーが正しく応答しているか確認します。

HTTPステータスコードを返します（成功した場合は`200`）およびメッセージを表示します。

# 例

```jldoctest
julia> check_gn()
GeneNetwork is alive.
200
```
