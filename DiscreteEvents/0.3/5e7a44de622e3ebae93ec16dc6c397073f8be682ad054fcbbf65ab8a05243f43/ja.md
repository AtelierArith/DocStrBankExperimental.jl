```
periodic!([clk], ex, Δt; <keyword arguments>)
periodic!(clk, ex; <keyword arguments>)
```

アクション `ex` をクロックのサンプリングレートで定期的に実行するように登録します。

# 引数

  * `clk<:AbstractClock`: 指定しない場合、𝐶 に登録されます。
  * `ex<:Action`: 式または関数、またはそれらのタプル。
  * `Δt<:Number=clk.Δt`: クロックのサンプリングレートを設定します。Δt が指定されていない場合、現在のサンプリングレートを使用します。≤ 0 の場合、正の値を計算します。

# キーワード引数

  * `cid::Int=clk.id`: cid ≠ clk.id の場合、id == cid の並列クロックでサンプリングします。これは `spawn` を上書きします。
  * `spawn::Bool=false`: true の場合、定期的なイベントを他の利用可能なスレッドにスローします。
