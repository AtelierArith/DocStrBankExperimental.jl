```
settext(text, pos;
    halign = "left",
    valign = "bottom",
    angle  = 0, # 度!
    markup = false)

settext(text;
    kwargs)
```

`pos`で`text`を描画します（省略した場合は`0/0`がデフォルトです）。フォントが指定されていない場合、macOSではデフォルトフォントはTimes Romanです。

テキストを整列させるには、`halign`を使用します。これは"left"、"center"、または"right"のいずれかで、`valign`は"top"、"center"、または"bottom"のいずれかです。

`angle`は回転を示します - Luxorのデフォルトの時計回り（+x軸から+y軸）ラジアンではなく、反時計回りの度数です。

`markup`が`true`の場合、文字列にはいくつかのHTMLスタイルのマークアップを含めることができます。サポートされているタグには以下が含まれます：

`<b>`, `<i>`, `<s>`, `<sub>`, `<sup>`, `<small>`, `<big>`, `<u>`, `<tt>`, および `<span>`

`<span>`タグには次のようなものを含めることができます：

```
<span font='26' background='green' foreground='red'>読み取れないテキスト</span>
```
