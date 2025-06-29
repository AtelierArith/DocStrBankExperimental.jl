与えられた有理数の調和展開を `1/2 + 1/3 + ...` の形の分数の和に展開し、与えられた有理数が調和数列の和として表現できない場合は `efgreedy` を使用して展開の残りを結論付けます。

第二引数が指定されている場合、展開はその値を最初の分母として使用して始まります。言い換えれば、`efharmonic(r)` は `[2, 3, ...]` で始まる配列を返しますが、`efharmonic(r, 3)` は `[3, 4, ...]` で始まる配列を返します。

この関数は、第二引数 `f ≤ 1` の場合に例外をスローします。

この関数は、展開の分母のみを返します（すなわち、`[a_1, a_2, ...]` のみ）。与えられた有理数 `r` が `r ≥ 1` を満たす場合、展開の最初の `n` 要素は 1 であり、ここで `n = floor(r)` です。与えられた有理数 `r` が `r < 0` を満たす場合、返されるすべての分母は 0 より小さくなり、次の関係が常に成り立ちます。

```
r == sum(1 .// efharmonic(r))
```
