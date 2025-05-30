```
writenewick(net)
writenewick(net, filename)
writenewick(net, IO)
```

ネットワークの親hesis拡張Newick形式を文字列としてファイルまたはIOバッファ/ストリームに書き込みます。オプションの引数（デフォルト値）：

  * di (false): Dendroscope用の形式で書き込む
  * round (false): ブランチ長と遺伝的特性γを丸める
  * digits (3): 丸めのための小数点以下の桁数
  * append (false): trueの場合、ファイルに追加
  * internallabel (true): trueの場合、内部ノードラベルを書き込む

現在のルート配置が許可されていない場合、他の配置が試みられます。成功した場合、ネットワークはこの新しいルート配置で更新されます。

低レベルの関数[`writesubtree!`](@ref)を使用します。
