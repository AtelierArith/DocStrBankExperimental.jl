```
solve!(kkt::AbstractKKTSystem, w::AbstractKKTVector)
```

KKTシステム$K x = w$を、`kkt`内に保存された線形ソルバーを使用して解決し、結果を`AbstractKKTVector` `w`内にインプレースで保存します。
