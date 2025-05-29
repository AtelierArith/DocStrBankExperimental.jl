```
indexweight(self::RheoTimeData; elperiods::Vector{K}, time_boundaries::Union{Nothing, Vector{T}} = nothing, includelast=true) where {K<:Integer,T<:Real}
```

この関数は、`modelfit`、`modelstepfit`、または`modeldiffeqfit`関数に送信できる配列インデックス（すなわち整数の配列）を返し、一定のサンプルレートを維持しながら重み付けされたフィッティングを提供します。

`time_boundaries`は`elperiods`よりも1つ多くのエントリを持っている必要があり、すべての重み付けセクションが開始点と終了点によって完全に定義されるようにします。

`indexweight`はインデックスを過小評価または過大評価することができます。指定された境界の`elperiods`が負の場合、すべての`abs(n)`インデックスが使用されます。ここで、`n`は指定された境界に対応する`elperiod`です。`n`が正の場合、インデックスは`n`回複製され、フィッティング手順中により高い重み付けが与えられます。期間ごとの要素数（`elperiods`）が`1`または`-1`の場合、その境界の元のインデックスが返されますが、`0`は`elperiods`の有効な引数として受け入れられません。

最後の要素は含まれる場合と含まれない場合があります。デフォルトでは最後の要素は強制的に含まれますが、キーワード引数`includelast=false`を提供することでこれを否定することができます。
