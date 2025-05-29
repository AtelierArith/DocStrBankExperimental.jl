```
dbootdata(data::T , bi::BootInput)::Vector{T}
dbootdata(data::T ; kwargs...)::Vector{T}
```

入力データの再サンプリングされたデータセットを、BootInputで定義された依存ブートストラップ手法を使用して取得します。

BootInputのキーワードコンストラクタを呼び出すキーワードメソッドも提供されています。利用可能なキーワードの詳細については、REPLで?BootInputを使用してください。

この関数は常に出力タイプVector{T}を持つことに注意してください。
