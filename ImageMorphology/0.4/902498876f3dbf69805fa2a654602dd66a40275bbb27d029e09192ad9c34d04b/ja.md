```
high_leveling(op, marker, mask; [dims])
high_leveling(op, marker, mask, se)
```

関数 g は、関数 f の上位レベリングであるのは、隣接する任意のピクセルの組 (p, q) に対して g(p)>g(q) -> g(p)<=f である場合に限ります。このアルゴリズムは、marker を ref の上位レベリングに変更します。

`dims` キーワードは、ボックス形状の構造要素 [`strel_box(marker; dims)`](@ref strel_box) を構築することによって処理する次元を指定するために使用されます。一般的な構造要素の場合、半サイズは各次元に沿って `0` または `1` であることが期待されます。

# 参照

[`low_leveling`](@ref),[`leveling`](@ref),  [`underbuild`](@ref),[`overbuild`](@ref)

# 参考文献

  * [1] 'From connected operators to levelings' [Meyer,1998] ISMM '98: 数学的形態学とその画像および信号処理への応用に関する第4回国際シンポジウムの議事録 1998年6月 ページ 191–198
  * [2] 'Mathematical Morphology: From Theory to Applications' chap6 [Serra et al.] https://doi.org/10.1002/9781118600788.ch8
