```
tf = pole_zero_cancellation(tf, verbose=false, digits=8)
```

極と零のペアを見つけて、極 = 零となるペアをキャンセルした新しい伝達関数を返します。これは、極と零を `isapprox` で比較することによって達成され、極と零は `digits` 桁に丸められます（再構成にも適用されます）。

# 引数

  * `tf::TransferFunction`: 伝達関数
  * `verbose::Bool=false`: どの極と零がキャンセルされたかを表示します。
  * `digits::Int`: 極と零を丸める桁数。 (i) キャンセルと (ii) 再構成のため。

# 例

```jldoctest
pole_zero_cancellation(s * (s - 1) / (s * (s + 1)))
# 出力
1.0*s - 1.0
-----------
1.0*s + 1.0
```
