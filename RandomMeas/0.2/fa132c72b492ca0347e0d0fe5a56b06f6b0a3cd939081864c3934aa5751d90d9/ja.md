```
get_trace(ρ::MPO)
```

行列積演算子 (MPO) ρ のトレースを計算するには、各テンソルをデルタ関数で収束させ、未プライムインデックスとプライムインデックスを等しくします。

# 引数

  * `ρ::MPO`: 量子状態または演算子を表す行列積演算子。

# 戻り値

ρ のトレースを表すスカラー。

# 例

```julia
t = get_trace(ρ)
```
