`NomnomlJS`パッケージは、`.noml`文字列からUMLダイアグラムをレンダリングするための`nomnoml` JavaScriptライブラリへのインターフェースを提供します。また、`read(filename, Diagram)`オーバーロードを介しても使用できます。

このパッケージの公開インターフェースは`Diagram`型であり、`nomnoml`ダイアグラムを構築します。このオブジェクトは、`write(filename, diagram)`を介していくつかの異なるファイル形式に書き込むことができます。

以下のサポートされている構文と機能のリストは、上流リポジトリ[nomnoml](https://github.com/skanaar/nomnoml)から引用されています。

### 関連タイプ

```plaintext
-    association
->   association
<->  association
-->  dependency
<--> dependency
-:>  generalization
<:-  generalization
--:> implementation
<:-- implementation
+-   composition
+->  composition
o-   aggregation
o->  aggregation
--   note
-/-  hidden
_>   weightless edge
__   weightless dashed edge
```

### 分類子タイプ

```plaintext
[name]
[<abstract> name]
[<instance> name]
[<reference> name]
[<note> name]
[<package> name]
[<frame> name]
[<database> name]
[<start> name]
[<end> name]
[<state> name]
[<choice> name]
[<sync> name]
[<input> name]
[<sender> name]
[<receiver> name]
[<transceiver> name]
[<actor> name]
[<usecase> name]
[<label> name]
[<hidden> name]
[<table> name| a | 5 || b | 7]
```

### ディレクティブ

```plaintext
#import: my-common-styles.nomnoml
#arrowSize: 1
#bendSize: 0.3
#direction: down | right
#gutter: 5
#edgeMargin: 0
#gravity: 1
#edges: hard | rounded
#background: transparent
#fill: #eee8d5; #fdf6e3
#fillArrows: false
#font: Calibri
#fontSize: 12
#leading: 1.25
#lineWidth: 3
#padding: 8
#spacing: 40
#stroke: #33322E
#title: filename
#zoom: 1
#acyclicer: greedy
#ranker: network-simplex | tight-tree | longest-path
```

### カスタム分類子スタイル

"."で始まるディレクティブは、分類子スタイルを定義します。スタイルは、修飾子とキー/値ペアのスペース区切りリストとして記述されます。

```plaintext
#.box: fill=#8f8 dashed
#.blob: visual=ellipse title=bold
[<box> GreenBox]
[<blob> HideousBlob]
```

修飾子

```plaintext
dashed
empty
```

キー/値ペア

```plaintext
fill=(any css color)

stroke=(any css color)

align=center
align=left

direction=right
direction=down

visual=actor
visual=class
visual=database
visual=ellipse
visual=end
visual=frame
visual=hidden
visual=input
visual=none
visual=note
visual=package
visual=receiver
visual=rhomb
visual=roundrect
visual=sender
visual=start
visual=table
visual=transceiver
```

スタイルのタイトルとテキスト本文は、カンマ区切りのテキスト修飾子のリストで装飾します。

```plaintext
title=left,italic,bold
body=center,italic,bold
```

テキスト修飾子

```plaintext
bold
center
italic
left
underline
```
