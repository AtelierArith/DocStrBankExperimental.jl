```
clear!(g::Genotypes)
clear!(v::BgenVariant)
```

キャッシュされた非圧縮バイト表現、確率、および投与量をクリアします。`BgenVariant`が指定されている場合は、対応する`.genotypes`を完全に削除します。
