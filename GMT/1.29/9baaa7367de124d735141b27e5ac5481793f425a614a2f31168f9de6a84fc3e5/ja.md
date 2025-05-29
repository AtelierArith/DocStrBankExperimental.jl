```
J = function imsegment(I::GMTimage{<:UInt8, 3}; maxdist::Int=0, maxcolors::Int=0, selsize::Int=3, colors::Int=5)::GMTimage
```

教師なしRGBカラーセグメンテーション。

詳細については、Leptonicaの関数 $pixColorSegment$ のドキュメントを参照してください（src/colorseg.c内）。

### 引数

  * `I::GMTimage{<:UInt8, 3}`: 入力RGB画像。

### キーワード引数

  * `maxdist::Int=0`: 既存のクラスタへの最大ユークリッド距離。
  * `maxcolors::Int=0`: 最初のパスで許可される最大色数。
  * `selsize::Int=3`: ノイズを除去するためのクロージング用構造要素のサイズ。
  * `colors::Int=5`: 4回目のパス後に許可される最終的な色数。

非常に粗いガイドライン（Leptonicaのドキュメント）として、ターゲット値 `colors` に対して、`maxdist` と `maxcolors` のおおよその値は次の通りです：

| `colors` | `maxcolors` | `maxdist` |
| --------:| -----------:| ---------:|
|        2 |           4 |       150 |
|        3 |           6 |       100 |
|        4 |           8 |        90 |
|        5 |          10 |        75 |
|        6 |          12 |        60 |
|        7 |          14 |        45 |
|        8 |          16 |        30 |

### 戻り値

セグメンテーションされた新しいインデックス付き `GMTimage`。

### 例

これは単純な例として考えられましたが、少しトリッキーな結果を示すことが判明しました。画像 "bunny_cenora.jpg" はシンプルで、6色しかないことが明確にわかりますので、$colors=6$ でうまくいくと期待されます。しかし実際には、アウトライン（黒）が2つの異なる（暗い）色として選ばれるため、$colors=7$ に設定する必要があります。

```julia
I = gmtread(TESTSDIR * "assets/bunny_cenora.jpg");
J = imsegment(I, colors=7);
grdimage(I, figsize=6)
grdimage!(J, figsize=6, xshift=6, show=true)
```
