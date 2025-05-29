```
compose(b, a; normalize_stepsize=false)
```

B系列 `a` を B系列 `b` と合成します。B系列 `b` は空の木の係数が1であると仮定されています。

Chartier、Hairer、Vilmart（2010）の表記法では、`compose(b, a) = b ⋅ a` となります。これは、メソッド `b` が最初に適用され、その後にメソッド `a` が適用されることを意味します。

`normalize_stepsize = true` の場合、返される B系列の係数は、各根付き木 `t` に対して `2^order(t)` で割られます。これにより、ステップサイズが正規化され、結果として得られる数値積分器 B系列は、入力系列と同じステップサイズを使用します（倍のステップサイズではなく）。

# 参考文献

以下のセクション3.1

  * Philippe Chartier, Ernst Hairer, Gilles Vilmart (2010) Algebraic Structures of B-series. Foundations of Computational Mathematics [DOI: 10.1007/s10208-010-9065-1](https://doi.org/10.1007/s10208-010-9065-1)
