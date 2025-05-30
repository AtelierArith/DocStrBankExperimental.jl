```
redirect_stdin([stream]) -> stream
```

[`redirect_stdout`](@ref)と同様ですが、[`stdin`](@ref)用です。ストリームの方向が逆になっていることに注意してください。

!!! note
    `stream`は、`IOStream`、`TTY`、`Pipe`、ソケット、または`devnull`などの互換性のあるオブジェクトでなければなりません。


他に[`redirect_stdio`](@ref)も参照してください。
