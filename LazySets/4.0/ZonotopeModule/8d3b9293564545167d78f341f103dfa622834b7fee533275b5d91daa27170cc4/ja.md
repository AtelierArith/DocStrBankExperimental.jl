```
remove_zero_generators(Z::Zonotope)
```

ゼロの生成子を削除した新しいゾノトープを返します。

### 入力

  * `Z` – ゾノトープ

### 出力

ゼロの生成子がない場合、結果は元のゾノトープ `Z` です。そうでない場合、結果は `Z` の中心と生成子を持つ新しいゾノトープで、ゼロの生成子は除外されます。
