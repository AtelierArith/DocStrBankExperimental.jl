```
integrate([func=(u_node,equations)->u_node,] u_ode, semi::AbstractSemidiscretization; normalize=true)
```

`func(u_node, equations)`を`u_ode`内の各ノード変数ベクトル`u_node`に対して呼び出し、その結果を半離散化`semi`に関連付けられた数値積分を使用して統合します。

`normalize`がtrueの場合、結果は計算領域の総体積で割られます。
