```
NoShow(layer)
NoShow(string, layer)
```

これは、Fluxモデルの一部の複雑さを隠すために、印刷（たとえばREPLプロンプトで）を変更します。モデルの実行には影響しません。

デフォルトでは、指定されたレイヤーの代わりに `NoShow(...)` を印刷します。文字列を提供すると、それが代わりに印刷されます – それは何でも構いませんが、同じ構造を再作成する関数の名前を印刷するのが理にかなっているかもしれません。

# 例

```jldoctest
julia> Chain(Dense(2 => 3), NoShow(Parallel(vcat, Dense(3 => 4), Dense(3 => 5))), Dense(9 => 10))
Chain(
  Dense(2 => 3),                        # 9 parameters
  NoShow(...),                          # 36 parameters
  Dense(9 => 10),                       # 100 parameters
)                   # Total: 8 arrays, 145 parameters, 1.191 KiB.

julia> pseudolayer((i,o)::Pair) = NoShow(
                                    "pseudolayer($i => $o)",
                                    Parallel(+, Dense(i => o, relu), Dense(i => o, tanh)),
                                  )
pseudolayer (generic function with 1 method)

julia> Chain(Dense(2 => 3), pseudolayer(3 => 10), Dense(9 => 10))
Chain(
  Dense(2 => 3),                        # 9 parameters
  pseudolayer(3 => 10),                 # 80 parameters
  Dense(9 => 10),                       # 100 parameters
)                   # Total: 8 arrays, 189 parameters, 1.379 KiB.
```
