```
control_dependencies(f, ops::Union{Array{PyObject}, PyObject})
```

ブロック内で*作成された*操作の前に、`ops`内のすべての操作を実行します。

```julia
op1 = tf.print("print op1")
op3 = tf.print("print op3")
control_dependencies(op1) do
    global op2 = tf.print("print op2")
end
run(sess, [op2,op3])
```

この例では、`op1`は`op2`の前に実行されなければなりません。しかし、`op3`がいつ実行されるかは保証されていません。プログラムの出力にはいくつかの可能性があります。

```julia-repl
print op3
print op1
print op2
```

または 

```
print op1
print op3
print op2
```
