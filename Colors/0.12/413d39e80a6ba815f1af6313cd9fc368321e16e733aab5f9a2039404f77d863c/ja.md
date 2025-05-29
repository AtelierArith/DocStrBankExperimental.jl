```
DE_CMC()
DE_CMC(kl, kc)
```

CMC方程式（CMC l:c）を使用してメトリックを構築します。重み付けパラメータ `kl` と `kc` を使用します。提供されない場合、これらのパラメータはデフォルトで `1` になります。

!!! note
    `DE_CMC` は準メトリックであり、すなわち対称性を破ります。したがって、`colordiff(a, b, metric=DE_CMC())` は `colordiff(b, a, metric=DE_CMC())` と等しくない場合があります。

