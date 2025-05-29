```
visualize(<arguments>; <keyword arguments>) -> Plot
```

必要なシミュレーションを実行して収集した出力からプロットを作成します。`simulate`と`plot`を一緒に実行する便利な関数です。

参照: [`visualize!`](@ref), [`simulate`](@ref), [`plot`](@ref), [`manipulate`](@ref)

# 例

```julia-repl
julia> @system S(Controller) begin
           a(a) => a ~ accumulate(init=1)
       end;

julia> visualize(S, :time, :a; stop=5, kind=:line)
       ┌────────────────────────────────────────┐
    32 │                                       :│
       │                                      : │
       │                                     :  │
       │                                    :   │
       │                                   :    │
       │                                  :     │
       │                                 :      │
  a    │                                :       │
       │                              .'        │
       │                            .'          │
       │                          .'            │
       │                       ..'              │
       │                   ..''                 │
       │             ....''                     │
     1 │.........''''                           │
       └────────────────────────────────────────┘
       0                                        5
                      time (hr)
```
