```
eachsequence(X::AbstractAlignment[, indices]; skip)
```

`X`のシーケンスに対するイテレータを返します。`indices`が指定されている場合、対応するインデックスのシーケンスのみを考慮します。整数引数`skip`を使用して、`skip`ごとに1つのシーケンスのみを返します（〜 `1:skip:end`）。
