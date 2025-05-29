```
AbstractAccelerator
```

非拡張演算子 `g` の固定点反復 g = g(x) を加速するために使用できる加速オブジェクトの抽象スーパタイプです。これらは、固定点アルゴリズムと通信するために以下のメソッドを実装する必要があります：

  * update!(aa::AbstractAccelerator, g, x, num_iter) #固定点反復を保存します
  * accelerate!(g::AbstractVector, x, aa::AbstractAccelerator, num_iter) #過去の反復を再結合して加速された点を決定し、`g` を上書きします
  * restart!(aa::AbstractAccelerator, args...; kwargs...) #アルゴリズムが加速器に再起動を指示します

アルゴリズムは以下の情報を照会できる必要があります：

  * was_successful(aa::AbstractAccelerator) –> Bool #最後の反復で accelerate! が成功したかどうかを示します

以下のメソッドはオプションです：

  * log!(aa::AbstractAccelerator, args...; kwargs...) #アルゴリズムが加速器にデバッグ用の特定の情報をログするよう指示します
