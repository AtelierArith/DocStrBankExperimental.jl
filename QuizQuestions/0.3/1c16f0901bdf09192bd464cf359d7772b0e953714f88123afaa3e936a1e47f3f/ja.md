```
hotspotq(imagefile, xs, ys=(0,1); label="", hint="", explanation="",
    correct_answer=nothing)
```

画像の指定された領域をユーザーがクリックしたかどうかを確認するための質問タイプ。

  * `imgfile`: 画像のファイル。画像はウェブページにエンコードされて埋め込まれます。
  * `xs`: `(xmin, xmax)`を指定する反復可能なオブジェクトで、`0 <= xmin <= xmax <= 1`を満たす必要があります。
  * `ys`: `(ymin, ymax)`を指定する反復可能なオブジェクト。
  * `correct_answer`: 回答が正しいかどうかをテストするために、より複雑なロジックを追加するために指定できるJavaScriptのテキストスニペット。クリックの座標には`x`と`y`を使用する必要があります。

## 例

```
using Plots
p1 = plot(x -> x^2, axis=nothing, legend=false)
p2 = plot(x -> x^3, axis=nothing, legend=false)
p3 = plot(x -> -x^2, axis=nothing, legend=false)
p4 = plot(x -> -x^3, axis=nothing, legend=false)
l = @layout [a b; c d]
p = plot(p1, p2, p3, p4, layout=l)
imgfile = tempname() * ".png"
savefig(p, imgfile)
hotspotq(imgfile, (0,1/2), (0, 1/2), label="``f(x) = -x^4``のグラフに最もよく一致するものは何ですか？")
```

!!! note
    この質問タイプでは画像の表示が調整されず、別途管理する必要があります。

