```julia
sigprocmask() -> cur
```

は、現在のブロックされたシグナルのセットを返します。ブロックされたシグナルのセットを変更するには、次のように呼び出します：

```julia
sigprocmask(how, set)
```

ここで、`set` は [`SigSet`](@ref) マスクであり、`how` は `set` を解釈する方法を指定するパラメータです：

  * `IPC.SIG_BLOCK`: ブロックされたシグナルのセットは、現在のセットと `set` 引数の和集合です。
  * `IPC.SIG_UNBLOCK`: `set` に含まれるシグナルは、現在のブロックされたシグナルのセットから削除されます。ブロックされていないシグナルのブロック解除を試みることは許可されています。
  * `IPC.SIG_SETMASK`: ブロックされたシグナルのセットは、引数 `set` に設定されます。

詳細については、[`sigprocmask!`](@ref) を参照してください。
