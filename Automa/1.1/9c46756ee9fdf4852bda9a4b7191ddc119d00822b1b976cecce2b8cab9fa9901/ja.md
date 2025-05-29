```
compile(re::RE; optimize::Bool=true, unambiguous::Bool=true)::Machine
```

`re` から有限状態機械 (FSM) をコンパイルします。`optimize` が真の場合、FSM の状態数を最小化しようとします。`unambiguous` が真の場合、動作が決定的でない FSM の作成を禁止します。

# 例

```
machine = let
    name = re"[A-Z][a-z]+"
    first_last = name * re" " * name
    last_first = name * re", " * name
    compile(first_last | last_first)
end
```
