```
imshow(arg1; kw...)
```

は、GMTgrid、GMTimage、浮動小数点数または文字列の2D配列（グリッドまたは画像のファイル名を含む）を受け入れる[`grdimage`](modules/grdimage) [`grdview`](modules/grdview)プログラムへのシンプルなフロントエンドです。*grdimage*および*grdview*プログラムの通常のオプションもここで適用されますが、提供されていない場合は適切な必要なパラメータを巧妙に推測します。他の画像生成モジュールとは異なり、画像を表示するために「show」キーワードは必要ありません。ここではデフォルトで設定されています。ユーザーが*imshow*を使用してより複雑な図のレイヤーを作成したい場合は、中間レイヤーに対して*show=false*を使用できます。

このモジュールは、`grdimge`、`grdview`、または`plot`を使用するかどうかを決定する内部ロジックを使用します。具体的には、`view`オプションが使用されると`grdview`が選択され、デフォルトの垂直スケールが割り当てられます。しかし、時には回転したプロットが必要で、オプションで傾けることはできますが、3Dビューではない場合があります。その場合は、`flat=true`オプションを使用して`grdimage`の使用を強制します。

# 例

```julia-repl
# メキシカンハットの垂直陰影照明ビューをプロット
julia> G = gmt("grdmath -R-15/15/-15/15 -I0.3 X Y HYPOT DUP 2 MUL PI MUL 8 DIV COS EXCH NEG 10 DIV EXP MUL =");
julia> imshow(G, shade="+a45")

# 上記と同じですが、自動輪郭を追加
julia> imshow(G, shade="+a45", contour=true)

# ランダムなヒートマップをプロット
julia> imshow(rand(128,128))

# ウェブからダウンロードしたjpeg画像を正弦投影にラップして表示
julia> imshow(gmtread()"http://larryfire.files.wordpress.com/2009/07/untooned_jessicarabbit.jpg"), region=:global, frame="g", proj=:sinu)

# 3Dビューの場合のキューブの壁に画像をプロットします。ファイル名は存在するものに置き換えてください。
julia> viz(G, zsize=6, facades=(GMT.TESTSDIR*"assets/cenora_base.jpg", GMT.TESTSDIR*"bunny_cenora.webp", GMT.TESTSDIR*"burro_cenora.webp"))
```

参照: [`grdimage`](@ref), [`grdview`](@ref)
