# 比較

モデルのwaicとpsisの値を比較します。

```julia
compare(m, ; mnames)

```

### 必要な引数

```julia
* `models`                             : ログ確率行列のベクトル
* `criterium`                          : ::Val{:waic} または ::Val{:psis} のいずれか
```

### オプションの引数

```julia
* `mnames::Vector{Symbol}`             : モデル名のベクトル
```

### 戻り値

```julia
* `df`                                 : 統計を含むDataFrame
```
