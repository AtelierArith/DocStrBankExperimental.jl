```
Container{T}
```

`struct` オブジェクトをシリアライズ/デシリアライズする際の中間コンテナ。

```
Container{T}()
```

`T` のための初期化されていないコンテナを作成します。

# 例

```jldoctest
julia> Container{Complex{Int64}}()
Container{Complex{Int64}}:
  re: Int64 = #undef
  im: Int64 = #undef
```
