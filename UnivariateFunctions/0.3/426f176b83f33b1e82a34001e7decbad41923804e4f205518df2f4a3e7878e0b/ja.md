```
years_between(a::Union{DateTime,Date}, b::Union{DateTime,Date})
```

2つの日付の間の年数。この値はスカラーとして返され、1年を365.2422日と仮定します。

### 入力

  * `a` - 終了日
  * `b` - 開始日。

### 返り値

  * `Real`。
