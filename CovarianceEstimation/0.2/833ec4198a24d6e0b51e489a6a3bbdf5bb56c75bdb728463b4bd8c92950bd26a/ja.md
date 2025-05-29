```
定常相関
```

線形シュリンクのターゲット: `target_F` を参照してください。`LinearShrinkageTarget` のサブタイプで、次のようになります。

  * $$
    F_{ij}=S_{ij}
    $$

    もし $i=j$ の場合、そして
  * $$
    F_{ij}=\overline{r}\sqrt{S_{ii}S_{jj}}
    $$

    それ以外の場合、ここで $\overline{r}$ は平均サンプル相関です。
