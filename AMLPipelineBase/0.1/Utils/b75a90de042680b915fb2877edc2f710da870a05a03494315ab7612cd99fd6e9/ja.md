```
find_catnum_columns(instances::DataFrame,maxuniqcat::Int=0)
```

すべてのカテゴリカルおよび数値列を見つけます。カテゴリカル列は、Real型ではないか、すべての要素がRealに対応しない列です。また、ユニークインスタンスのサイズが`maxuniqcat`未満の列もカテゴリカルと見なされます。
