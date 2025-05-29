```
convert_flow_type_symbol(::Client, flow_type::Union{ForwardFlow,BackwardFlow})
```

この関数は、フロータイプ（ForwardFlowまたはBackwardFlowのいずれか）をシンボルに変換します。変換プロセスは、フロータイプを文字列に変換し、括弧を削除し、「Flow」の前にアンダースコアを追加し、小文字に変換し、最後にシンボルに変換することを含みます。

# 引数

  * `::Client`: Clientオブジェクト。
  * `flow_type::Union{ForwardFlow,BackwardFlow}`: 変換されるフロータイプ。

# 戻り値

  * フロータイプを表すシンボル。

# 例

```julia
client = Client()
flow_type = ForwardFlow()
flow_sym = convert_flow_type_symbol(client, flow_type)
```
