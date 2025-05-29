```
shutdown(a::Agent)
```

この関数はエージェントが終了するときに呼び出されます。エージェントは、必要に応じて終了処理を行うメソッドを提供することができます。

# 例:

```julia
using Fjage

@agent struct MyAgent end

function Fjage.shutdown(a::MyAgent)
  @info "MyAgent shutting down"
end
```
