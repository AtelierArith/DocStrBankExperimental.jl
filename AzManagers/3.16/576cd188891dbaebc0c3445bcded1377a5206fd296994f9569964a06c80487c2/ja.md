```
f = machine_preempt_channel_future(pid)
```

もし存在すれば、プロセスID `pid` のチャネル割り当てに対する Future を返し、これは `pid` の VM プリエンプションを通信するために使用されます。ワーカーがプリエンプトされると、Bool がチャネルに置かれます。したがって、コードはこれが発生したときに検出し、`pid` に対応するマシンが削除される前に適切なアクションを取ることができます。

# 例

```julia
addproc2(template, 2; spot=true)

f = machine_preempt_channel_future(workers()[1])

remote_do(pid, f) do
    c = fetch(f)::Channel{Bool}
    while true
        if isready(c)
            @info "VM がプリエンプトされています"
            break
        end
        sleep(1)
    end
end
```
