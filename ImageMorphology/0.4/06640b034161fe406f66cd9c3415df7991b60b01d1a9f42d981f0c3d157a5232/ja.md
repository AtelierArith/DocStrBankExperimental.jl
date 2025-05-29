画像の最大木形態表現。

# 詳細

*しきい値処理*操作を考えてみましょう。

```julia
    mask = [val ≥ threshold for val in image]
```

`mask`内の接続成分（隣接する真の値の集合）を特定できます。*画像のしきい値処理*がすべての可能なしきい値に対して順次適用されると、*成分木*と呼ばれる階層構造に整理できる接続成分のコレクションが生成されます。値が1、2、3の1次元「画像」を考えてみましょう：

```
       2233233312223322
```

接続成分は次のようになります。

```
    1: AAAAAAAAAAAAAAAA
    2: BBBBBBBB.CCCCCCC
    3: ..DD.EEE....FF..
```

ここで、文字は結果として得られる接続成分のラベルであり、`.`はピクセル値がしきい値未満であることを示します。この例では、対応する*成分木*は次のようになります：

```
      A
     ⭩ ⭨
    B   C
   ⭩ ⭨   ⭨
  D   E   F
```

*最大木*は*成分木*の効率的な表現です。しきい値レベル$t$での接続成分$C$は、このレベルからの単一の*参照ピクセル*r*（`image[r] == t`）によって表され、これは$C$の他のすべてのピクセルの親であり、また高いしきい値での接続成分の*参照ピクセル*の親でもあり、これらは$C$の子です。私たちの例では、参照ピクセル（対応する成分の文字で示される）は次のようになります：

```
    1: ........A.......
    2: B........C......
    3: ..D..E......F...
```

すなわち、

| Comp | Ref.Pixel |
| ----:| ---------:|
|  *A* |         9 |
|  *B* |         1 |
|  *C* |        10 |
|  *D* |         3 |
|  *E* |         6 |
|  *F* |        13 |

したがって、全体の最大木は親ピクセルのインデックスのベクトルとしてエンコードできます：

```
9  1  1  3  1  1  6  6  9  9 10 10 10 13 10 10
```

*最大木*は、多くの形態学的演算子、特に接続演算子の基礎です。形態学的開閉とは異なり、これらの演算子は固定の構造要素を必要とせず、特定の基準を満たす柔軟な構造要素で作用します。

# 参照

[`area_opening`](@ref), [`area_closing`](@ref), [`diameter_opening`](@ref), [`diameter_closing`](@ref)。

# 参考文献

1. Salembier, P., Oliveras, A., & Garrido, L. (1998). *Antiextensive Connected Operators for Image and Sequence Processing*. IEEE Transactions on Image Processing, 7(4), 555-570.

    > https://doi.org/10.1109/83.663500
2. Berger, C., Geraud, T., Levillain, R., Widynski, N., Baillard, A., Bertin, E. (2007). *Effective Component Tree Computation with Application to Pattern Recognition in Astronomical Imaging*. In International Conference on Image Processing (ICIP), 41-44.

    > https://doi.org/10.1109/ICIP.2007.4379949
3. Najman, L., & Couprie, M. (2006). *Building the component tree in quasi-linear time*. IEEE Transactions on Image Processing, 15(11), 3531-3539.

    > https://doi.org/10.1109/TIP.2006.877518
4. Carlinet, E., & Geraud, T. (2014). *A Comparative Review of Component Tree Computation Algorithms*. IEEE Transactions on Image Processing, 23(9), 3885-3895.

    > https://doi.org/10.1109/TIP.2014.2336551
