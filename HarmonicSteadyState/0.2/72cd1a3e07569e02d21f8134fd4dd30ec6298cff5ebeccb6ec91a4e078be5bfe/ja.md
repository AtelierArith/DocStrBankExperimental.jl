```
TotalDegree
```

Total Degree ホモトピー法は、トリビアル多項式系 $F(x) =xᵢ^{dᵢ} +aᵢ$ からのホモトピー $H(x, t) = γ t G(x) + (1-t) F(x)$ を実行します。ここで、最大次数 $dᵢ$ は [ベズーの定理](https://en.wikipedia.org/wiki/B%C3%A9zout%27s_theorem) によって決定されます。この方法はすべての解を見つけることを保証しますが、高い計算コストが伴います。詳細については [HomotopyContinuation.jl](https://www.juliahomotopycontinuation.org/guides/totaldegree/) を参照してください。

# フィールド

  * `gamma::Complex`: ホモトピーのための開始系 G(x) の複素数乗算因子
  * `thread::Bool`: スレッドが有効かどうかを示すブール値。
  * `tracker_options::HomotopyContinuation.TrackerOptions`: トラッカーのオプション。
  * `endgame_options::HomotopyContinuation.EndgameOptions`: エンドゲームのオプション。
  * `compile::Union{Bool, Symbol}`: コンパイルオプション。
  * `seed::UInt32`: 乱数生成のためのシード。
