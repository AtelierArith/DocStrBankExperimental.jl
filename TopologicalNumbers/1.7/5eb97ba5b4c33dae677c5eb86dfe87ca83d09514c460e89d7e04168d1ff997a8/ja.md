```
LBFProblem(H, n, N)
```

デフォルトのパラメータを持つローカルベリーフラックス問題を構築します。

# 引数

  * `H`: システムを定義するハミルトニアン関数 `H=H(k)`。`k` は波数ベクトルの抽象ベクトル（またはタプル）です。`k` の次元は2でなければなりません。
  * `n`: ベリーフラックスを計算する際の波数 ($2\pi n/N$) を表す2つの `Int` 要素を含む `AbstractVector`（または `Tuple`）。`n` の次元は2でなければなりません。
  * `N`: ブリルアンゾーンの1方向の点の数。

# 戻り値

`LBFProblem` オブジェクト。

# 例

```julia
julia> 
```
