```
HierarchicalLogger(root_logger; [propagate] [, delimiter] [, min_logging_level])
```

`root_logger`をルートとする`HierarchicalLogger`を構築します。

# 引数

  * `root_logger::AbstractLogger`: ルートノードに関連付けられたロガー
  * `propagate::PropagateToChildren.Mode=PropagateToChildren.None`: ノードに送信されたメッセージがその子ノードにどのように伝播されるかを決定します
  * `delimiter::Char='.'`: ノードの文字列表現における親子区切り
  * `min_logging_level::LogLevel=All`: すべてのロガーの初期最小ログレベルを設定します
