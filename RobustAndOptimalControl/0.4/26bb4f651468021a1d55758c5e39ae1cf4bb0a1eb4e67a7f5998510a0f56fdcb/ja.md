```
add_resonant_disturbance(sys::StateSpace{Continuous}, ω, ζ, Ai::Int; measurement = false)
```

`sys`に共鳴擾乱モデルを追加します。

# 引数:

  * `ω`: 周波数
  * `ζ`: 相対減衰
  * `Ai`: 影響を受ける状態
  * `measurement`: trueの場合、擾乱は出力に作用し、これによりコントローラはωでゼロを持つことになります（多項式s² + 2ζωs + ω²の根）。falseの場合、擾乱は入力に作用し、これによりコントローラはωで極を持つことになります（多項式s² + 2ζωs + ω²の根）。
