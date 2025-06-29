```
closedloop(l::LQGProblem, L = lqr(l), K = kalman(l))
```

GladとLjungの式8.28で定義された閉ループシステム。注意、この閉ループの定義は、入力行列としてB2ではなくB1を持つlft(P, K)とは異なります。`lft(l)`を使用して、外乱から制御変数へのシステム`w -> z`を取得します。

返り値はフィルタされた参照からの閉ループのみであり、他の外乱信号（B1）は無視されます。より高度なオプションについては[`feedback`](@ref)を参照してください。この関数は、制御信号が`u = r̃ - Lx̂`（`u = L(xᵣ - x̂)`ではない）として計算されることを前提としています。つまり、フィードフォワード信号`r̃`は植物の入力に直接追加されます。したがって、`r̃`は状態参照を取り、フィードフォワード信号を出力する逆のようなモデルによって生成される必要があります。

`static_gain_compensation`を使用して、入力B2に作用する参照からのゲインを調整します。`dcgain(closedloop(l))*static_gain_compensation(l) ≈ I`
