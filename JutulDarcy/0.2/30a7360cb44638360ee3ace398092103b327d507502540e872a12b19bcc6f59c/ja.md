```
PhaseRelativePermeability(s, k; label = :w, connate = s[1], epsilon = 1e-16)
```

等しい長さのベクトル `s` と `k` として与えられたソートされた相相対透過率テーブルを格納する型：

$$
K_r = K(S)
$$

オプションで、相のラベル、コナート飽和度、および外挿を避けるために使用される小さなエプシロン値を指定できます。戻り値の型は、テーブル、相のコンテキスト、自動検出された臨界および最大相対透過率値の両方を保持し、基礎となる関数を評価するために飽和度の値を渡すことができます：

```jldoctest
s = range(0, 1, 50)
k = s.^2
kr = PhaseRelativePermeability(s, k)
round(kr(0.5), digits = 2)

# output

0.25
```
