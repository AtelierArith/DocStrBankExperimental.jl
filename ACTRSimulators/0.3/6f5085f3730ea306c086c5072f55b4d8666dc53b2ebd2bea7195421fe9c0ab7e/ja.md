```
retrieve!(actr, chunk, args...; kwargs...)
```

メモリの取得を完了し、chunkを宣言的メモリバッファに追加し、busy = falseおよびempty = falseを設定します。取得に失敗した場合、エラーはtrueに設定されます。

# 引数

  * `actr`: ACT-Rモデルオブジェクト
  * `request...`: スロット-値ペアの可変リスト
