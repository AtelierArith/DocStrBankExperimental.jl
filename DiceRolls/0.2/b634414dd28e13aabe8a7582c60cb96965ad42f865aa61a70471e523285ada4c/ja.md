```
values, frequency = histogram(dice; normalize=false)
values, frequency = histogram(roll; normalize=false)
```

サイコロまたはロールのヒストグラムを計算します。この操作は、内部の部分のヒストグラムを再帰的に計算するため、複雑なロールの場合は遅くなる可能性があります。
