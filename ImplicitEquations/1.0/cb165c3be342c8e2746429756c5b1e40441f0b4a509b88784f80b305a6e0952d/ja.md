関数をグラフ化するための、ASCII文字を使用した、2次元方程式に関連する述語（例えば `f == 0` または `f < g`）を描画する関数です。ここで `f` と `g` は関数であり、例えば `f(x,y) = y - sqrt(x)` です。位置引数 `L`, `R`, `B`, `T` は方程式のグラフのx-y範囲を示します。キーワード引数 `W` と `H` は使用するピクセルの数を示します。

`offset=0` に設定するとアルゴリズムが表示されます。

ピクセルは重要です。グラフはピクセルを次のように色付けします。

  * "白"（例：" "）は、ピクセルで示された領域に解が存在しない場合
  * "黒"（例："x"）は、領域に解が存在することが知られている場合
  * "赤"（例："."）は、解が*存在するかもしれない*場合

## 例

```
julia> f(x,y) = x^2 + y^2
f (generic function with 1 method)

julia> r = f ⩵ 4^2
ImplicitEquations.Pred(f, ==, 16)

julia> asciigraph(r)

     .xxxxx
    xx    xx
   x.      xx
  x.        xx
 xx          xx
 x            x
 x            x
 x            x
 x            x
 xx          x.
  xx        .x
   xx      .x
    xx    xx
     xxxxx.

```
