```
CommonCovariance
```

線形収縮のターゲット: `target_C`を参照してください。`LinearShrinkageTarget`のサブタイプであり、

  * $$
    F_{ij}=v
    $$

    もし $i=j$ で、$v=\mathrm{tr}(S)/p$ であり、
  * それ以外の場合は $F_{ij}=c$ で、$c=\sum_{i\neq j} S_{ij}/(p(p-1))$ です。
