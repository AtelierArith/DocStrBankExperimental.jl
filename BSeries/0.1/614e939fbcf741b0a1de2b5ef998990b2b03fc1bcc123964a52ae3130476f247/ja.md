```
bseries(mis::MultirateInfinitesimalSplitMethod, order)
```

多段階無限小分割法 `mis` の B-系列を指定された整数 `order` まで計算します。

!!! note "基本微分による正規化"
    このメソッドによって返される B-系列の係数は、時間ステップのべき乗を `symmetry` で割ったものと、入力ベクトル場 $f^\nu$ の対応する基本微分を掛ける必要があります。詳細は [`evaluate`](@ref) を参照してください。

