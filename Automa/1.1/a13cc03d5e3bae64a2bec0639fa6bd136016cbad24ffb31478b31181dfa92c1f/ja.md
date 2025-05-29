```
machine2dot(machine::Machine)::String
```

マシンのフローチャートをGraphviz（dot）形式の文字列で返します。`Graphviz`というコマンドラインツールを使用すると、dotファイルをさまざまな画像形式に変換できます。

# 例

```julia
open("/tmp/machine.dot", "w") do io
    println(io, machine2dot(machine))
end
# graphvizがインストールされている必要があります
run(pipeline(`dot -Tsvg /tmp/machine.dot`), stdout="/tmp/machine.svg")
```
