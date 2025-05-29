`system` は `ODESystem` を返す主要な展開/フラット化関数です。

```julia
system(a)
```

### 引数

  * `a` : ネストされた方程式のベクトルを含む入力モデル

### オプション/キーワード引数

  * `simplify = true` : 結果を簡素化するために `structural_simplify` が使用されるかどうか

### 戻り値

  * `::ODESystem` : フラット化されたモデル
