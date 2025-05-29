```
@message classname [performative] struct mtype [<: supertype]
  fields...
end
```

Create a message class from a fully qualified class name. If a performative is not specified, it is guessed based on the class name. For class names ending with "Req", the performative is assumed to be REQUEST, and for all other messages, INFORM.

# Examples

```julia-repl
julia> @message "org.arl.fjage.shell.MyShellExecReq" struct MyShellExecReq
         command::String
       end
julia> req = MyShellExecReq(command="ps")
MyShellExecReq:REQUEST[command:"ps"]
```
