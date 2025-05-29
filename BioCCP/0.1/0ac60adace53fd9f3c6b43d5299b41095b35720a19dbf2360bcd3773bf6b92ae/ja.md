```
std_minsamplesize(n::Integer; p=ones(n)/n, m::Integer=1, r=1, normalize=true)
```

各モジュールを少なくとも `m` 回観察するための最小設計数の標準偏差を計算します。

  * `n`: 設計空間内のモジュールの数
  * `p`: 異なるモジュールの確率または豊富さを持つベクトル
  * `m`: 収集する必要があるモジュールの完全なセットの数
  * `r`: 設計ごとのモジュールの数
  * normalize: true の場合、`p` を正規化します

## 例

```julia-repl
julia> n = 100
julia> std_minsamplesize(n; p=ones(n)/n, m=1, r=1, normalize=true)
126
```
