```
OptimalStringAlignment()
```

OptimalStringAlignment距離（制限付きDamerauLevenshtein距離とも呼ばれる）を作成します。

これは、1つの文字列を別の文字列に変更するために必要な操作の最小数（挿入、削除、または単一の文字の置換、または隣接する2つの文字の転置から成る）です。

この距離は、サブストリングが1回以上編集されないという制限を課すことによって、DamerauLevenshtein距離とはわずかに異なります。たとえば、「CA」から「ABC」への距離は、OptimalStringAlignment距離では3ですが、DamerauLevenshtein距離では2です。DamerauLevenshtein距離とは対照的に、OptimalStringAlignment距離は三角不等式を満たしません。
