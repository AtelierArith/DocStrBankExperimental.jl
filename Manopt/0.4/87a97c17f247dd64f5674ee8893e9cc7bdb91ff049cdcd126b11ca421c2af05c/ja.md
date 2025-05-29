```
 DouglasRachford!(M, f, proxes_f, p)
 DouglasRachford!(M, mpo, p)
```

マンifold $\mathcal M$ 上で Douglas-Rachford アルゴリズムを計算し、初期データ $p ∈ \mathcal M$ と (2つの) 近接マップ `proxes_f` を `p` の代わりに使用します。

$$
k>2
$$

の近接マップの場合、問題は並列 Douglas Rachford を使用して再定式化されます：ベクトル型の近接マップが冪マニフォールド $\mathcal M^k$ 上に導入され、2番目の近接マップは `mean` (リーマン中心) に設定されます。したがって、これは2つの近接マップに還元されますが、それぞれは並列で近接マップを評価します。つまり、ベクトル内の成分ごとに評価されます。

!!! note
    新しい出発点 `p'` を冪マニフォールド上に作成する際に、`p` のコピーが作成されるため、(k>2 によって暗黙的に生成された) 並列 Douglas Rachford は現在のところインプレースで動作しません。


代わりに [`ManifoldProximalMapObjective`](@ref) `mpo` を提供すると、近接マップは変更されません。

# 入力

  * `M`:        リーマン多様体 $\mathcal M$
  * `f`:        コスト関数の和からなるコスト関数
  * `proxes_f`: 近接マップを実行する形式 `(M, λ, p)->q` または `(M, q, λ, p)->q` の関数で、ここで `⁠λ` は各コスト関数の近接パラメータを示します。
  * `p`:        初期点 $p ∈ \mathcal M$

詳細については [`DouglasRachford`](@ref) を参照してください。 ```
