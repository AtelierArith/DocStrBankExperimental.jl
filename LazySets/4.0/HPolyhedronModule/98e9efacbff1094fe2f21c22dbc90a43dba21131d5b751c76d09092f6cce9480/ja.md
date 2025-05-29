# 拡張ヘルプ

```
σ(d::AbstractVector{M}, P::HPoly{N};
  solver=default_lp_solver(M, N) where {M, N}
```

### 入力

  * `solver` – （オプション、デフォルト: `default_lp_solver(M, N)`）線形計画を解くために使用されるバックエンド

### 出力

`P` が指定された方向で無限大の場合、2つのケースがあります：

  * `P` が `HPolytope` の場合、エラーをスローします。
  * `P` が `HPolyedron` の場合、結果には `±Inf` エントリが含まれます。
