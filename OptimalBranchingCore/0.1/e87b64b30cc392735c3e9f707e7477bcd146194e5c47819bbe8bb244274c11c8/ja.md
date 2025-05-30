```
covered_by(a::Integer, clause_or_dnf)
```

`a`が論理式`clause_or_dnf`によってカバーされているかを確認します。

### 引数

  * `a`: ビット文字列。
  * `clause_or_dnf`: 論理式で、[`Clause`](@ref)オブジェクトまたは[`DNF`](@ref)オブジェクトであることができます。

### 戻り値

`a`が`clause_or_dnf`を満たす場合は`true`、そうでない場合は`false`を返します。
