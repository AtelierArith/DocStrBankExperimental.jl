```
register_default_process!(process, m::Module; warn = true)
```

`process`（`Equation` または `Process`）を、指定されたモジュールによって追跡されるデフォルトプロセスのリストにおけるそのLHS変数のデフォルトプロセスとして登録します。`warn`がtrueの場合、同じLHS変数を持つデフォルトプロセスがすでに存在し、上書きされる場合は警告を投げます。

[`default_processes`](@ref)を使用して、追跡されているデフォルトプロセスのリストを取得できます。

!!! note "開発者向け"
    ProcessBasedModelling.jlに基づいた新しいモジュール/パッケージを開発している場合、その中でデフォルトプロセスを登録する場合は、`register_default_process!`の呼び出しをモジュールの`__init__()`関数内に囲むようにしてください。例えば：

    ```julia
    module MyProcesses
    # ...

    function __init__()
        register_default_process!.(
            [
                process1,
                process2,
                # ...
            ],
            Ref(MyProcesses)
        )
    end

    end # module
    ```

