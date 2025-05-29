```
@compounds
```

複数の化合物種を作成するマクロで、それぞれは小さな成分種で構成されています。`@compound`と同じ構文を使用しますが、各行に1つの化合物種があります。

例:

```julia
t = default_t()
@species C(t) H(t) O(t)
@compounds
    CH4(t) = C + 4H
    O2(t) = 2O
    CO2(t) = C + 2O
    H2O(t) = 2H + O
end
```

注意:

  * 成分種は`@compound`マクロを使用する前に定義されている必要があります。
