```
AbstractRecurrenceType
```

すべての再帰仕様タイプのスーパタイプ。サブタイプのインスタンスは、再帰を指定するために[`RecurrenceMatrix`](@ref)や類似のコンストラクタに渡されます。数値的な距離の閾値を抽出するには[`recurrence_threshold`](@ref)を使用します。

考えられるサブタイプは次のとおりです：

  * `RecurrenceThreshold(ε::Real)`: 再帰は、参照点からの距離が`≤ ε`である任意の点として定義されます。
  * `RecurrenceThresholdScaled(ratio::Real, scale::Function)`: ここで`scale`は距離行列`dm`（[`distancematrix`](@ref）を参照）に対する関数であり、再帰閾値`ε`の値をスケーリングするために使用されます。すなわち、`ε = ratio*scale(dm)`となります。新しい`ε`が得られた後、このメソッドは`RecurrenceThreshold`と同様に機能します。`scale`が`mean`または`maximum`の場合は、特化したバージョンが使用されます。
  * `GlobalRecurrenceRate(q::Real)`: ここでは、全体の行列に対する再帰率の合計数が、[`distancematrix`](@ref)の分位数`q ∈ (0,1)`として指定されます。実際には、これは入力軌道`x, y`に対して、合計`Nx * Ny`の中で（おおよそ）再帰の比率`q`をもたらします。
  * `LocalRecurrenceRate(r::Real)`: ここでの再帰閾値は点依存です。これは、`x`の各点が、合計可能な`N`の中で比率`r`の固定数の`k = r*N`の隣接点を持つように定義されています。同等に、これは再帰行列の各列が正確に`k`の真のエントリを持つことを意味します。`LocalRecurrenceRate`は、結果として得られる再帰行列が対称であることを保証しないことに注意してください。
