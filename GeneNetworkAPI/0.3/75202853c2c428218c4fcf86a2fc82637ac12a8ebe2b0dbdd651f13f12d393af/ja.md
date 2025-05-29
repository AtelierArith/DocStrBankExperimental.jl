```
gn_url()
```

デフォルトのGeneNetworkサーバーAPI URLを返します。

すべてのユーザーレベルの関数は、標準のURLとは異なるGeneNetworkサーバーのURLをオプションで受け取ることができ、別のサーバーインスタンスをクエリしたい場合に使用できます。

# 例

```jldoctest
julia> gn_url()
"https://genenetwork.org/api/v_pre1/"
```
