```
D3Tree(children, <キーワード引数>)
```

ブラウザやipythonノートブックで表示するためのツリーを構築し、子ノードのインデックスのリストで構造を指定します。

# 引数

## 必須

  * `children::Vector{Vector{Int}}`: 各ノードの子ノードのリスト。例:

    ```julia
    D3Tree([[2,3], [], [4], []])
    ```

    は4つのノードを持つツリーを作成します。ノード2と3はノード1の子であり、ノード4はノード3の唯一の子です。ノード2と4は子を持ちません。

## キーワード:

  * `text::Vector{String}` - 各ノードの下に表示されるテキスト。
  * `tooltip::Vector{String}` - 各ノードにマウスをホバーしたときに表示されるテキスト。
  * `style::Vector{String}` - 各ノードのhtmlスタイル。
  * `link_style::Vector{String}` - 各リンクのhtmlスタイル。
  * `title::String` - htmlタイトル。
  * `init_expand::Integer` - 初期に展開するレベル。
  * `init_duration::Number` - 初期アニメーションの持続時間（ms）。
  * `svg_height::Number` - ツリーを含むsvgの高さ（px）。

```
