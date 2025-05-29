```
sel = strel(nhood::Matrix{<:Integer})::Sel
```

または

```
sel = strel(name::String, par1::Int, par2::Int=0)::Sel
```

形態学的操作のための strel（構造要素）オブジェクトを作成します。

平坦な構造要素は、1のピクセルが形態学的計算に含まれ、0のピクセルは含まれないバイナリ値の近傍です。

### 引数

  * `nhood`: 0と1の行列でなければなりません。
  * `name`: 代わりに、次の中から構造要素の名前を指定できます：$“cross”$、$“disk”$、$“diamond”$、$“square”$、$“box”$、および$“rec”$または$“rectangle”$。
  * `par1`: $“disk”$および$“diamond”$の構造要素の半径と、残りのものの幅です。
  * `par2`: 提供された場合（高さ）、すべての構造要素は`par1 x par2`（幅 x 高さ）サイズの長方形になります。

### 戻り値

Sel型オブジェクト。
