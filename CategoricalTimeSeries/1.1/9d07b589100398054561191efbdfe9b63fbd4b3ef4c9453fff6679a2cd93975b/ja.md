```
print_results(m::IB, disp_thres = 0.1)
```

最適化された入力モデル 'm' のデータのクラスタリングを表示します。

IBアルゴリズムは決定論的ではないため、クラスタリング行列 'm.qt*x' のいくつかの確率はゼロではありません。可読性を高めるために、'disp*thres' 未満の確率はすべて 0 として表示され、それ以外はすべて 1 として表示されます。結果は 2D 行列で、行はクラスタを、列は初期カテゴリを表します。1 はどのクラスタにどのカテゴリが属するかを示します。単一のカテゴリに対して複数の 1 が存在する場合、それは最適化が選択した β 値に対してこのカテゴリに単一のクラスタを割り当てることができなかったことを意味します。異なる β を試すか、アルゴリズムの DIB バリアントを使用してみることができます。
