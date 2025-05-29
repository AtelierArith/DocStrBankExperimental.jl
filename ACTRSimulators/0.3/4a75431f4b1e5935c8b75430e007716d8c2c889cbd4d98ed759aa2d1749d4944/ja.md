```
attend!(actr, chunk, args...; kwargs...)
```

注意のシフトを完了し、`chunk`を視覚バッファに追加し、状態をbusy = falseおよびempty = falseに設定します。

# 引数

  * `actr`: ACT-Rモデルオブジェクト
  * `chunk`: メモリチャンク
