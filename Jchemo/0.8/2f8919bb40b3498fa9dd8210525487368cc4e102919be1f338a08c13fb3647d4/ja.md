```
aggsumv(x::Vector, y::Union{Vector, BitVector})
```

カテゴリ変数のクラスごとの小計を計算します。

  * `x` : 合計する定量変数 (n)
  * `y` : カテゴリ変数 (n) (クラスメンバーシップ)。

## 例

```julia
using Jchemo

x = rand(1000)
y = vcat(rand(["a" ; "c"], 900), repeat(["b"], 100))
aggsumv(x, y)
```
