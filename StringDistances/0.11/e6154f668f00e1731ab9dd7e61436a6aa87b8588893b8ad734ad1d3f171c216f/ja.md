```
SorensenDice(q::Int)
```

SorensenDice距離を作成します。

距離は次のように対応します。  

$$
1 - 2 * |Q(s1, q) ∩ Q(s2, q)|  / (|Q(s1, q)| + |Q(s2, q)|)
$$

ここで、$Q(s, q)$ は文字列sの長さnのq-グラムの集合を示します。
