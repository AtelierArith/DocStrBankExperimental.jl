```
control_dependencies(f, ops::Union{Array{PyObject}, PyObject})
```

Executes all operations in `ops` before any operations *created* inside the block. 

```julia
op1 = tf.print("print op1")
op3 = tf.print("print op3")
control_dependencies(op1) do
    global op2 = tf.print("print op2")
end
run(sess, [op2,op3])
```

In this example, `op1` must be executed before `op2`. But there is no guarantee when `op3` will be executed.  There are several possible outputs of the program such as

```julia-repl
print op3
print op1
print op2
```

or 

```
print op1
print op3
print op2
```
