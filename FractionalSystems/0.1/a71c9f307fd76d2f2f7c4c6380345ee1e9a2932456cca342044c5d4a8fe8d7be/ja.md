```
fotf2cotf(tf)
```

FOTFオブジェクトを同等の次数のオブジェクトに変換します。

### 例

```julia-repl
julia> fotf2cotf(G)
TransferFunction{Discrete{Int64}, ControlSystems.SisoRational{Float64}}   
2.0z^4 + 1.0z^3
---------------
2.0z^6 + 1.0z^5

サンプル時間: 2 (秒)
離散時間伝達関数モデル
```
