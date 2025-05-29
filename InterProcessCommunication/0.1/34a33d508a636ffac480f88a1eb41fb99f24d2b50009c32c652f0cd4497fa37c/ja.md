```julia
sigprocmask!(cur) -> cur
```

は、ブロックされた信号の現在のセットで `cur`（[`SigSet`](@ref）のインスタンス）を上書きし、それを返します。ブロックされた信号のセットを変更するには、次のように呼び出します：

```julia
sigprocmask!(how, set, old) -> old
```

これは、`how` と `set` に従ってブロックされた信号のセットを変更し（[`sigprocmask`](@ref)を参照）、以前のブロックされた信号のセットで `old`（[`SigSet`](@ref）のインスタンス）を上書きし、`old` を返します。

参照：[`sigprocmask`](@ref)。
