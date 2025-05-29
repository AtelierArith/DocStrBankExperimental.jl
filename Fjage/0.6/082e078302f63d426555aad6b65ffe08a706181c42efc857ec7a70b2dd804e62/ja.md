```
@message classname [performative] struct mtype [<: supertype]
  fields...
end
```

完全修飾されたクラス名からメッセージクラスを作成します。performativeが指定されていない場合は、クラス名に基づいて推測されます。"Req"で終わるクラス名の場合、performativeはREQUESTと見なされ、それ以外のメッセージの場合はINFORMと見なされます。

# 例

```julia-repl
julia> @message "org.arl.fjage.shell.MyShellExecReq" struct MyShellExecReq
         command::String
       end
julia> req = MyShellExecReq(command="ps")
MyShellExecReq:REQUEST[command:"ps"]
```
