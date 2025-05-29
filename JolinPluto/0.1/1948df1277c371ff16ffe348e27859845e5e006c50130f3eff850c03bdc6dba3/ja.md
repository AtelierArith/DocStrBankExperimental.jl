```
channel = ChannelPluto(10) do ch
    for i in 1:10
        put!(ch, i)
        sleep(1)
    end
end
```

通常の `Channel` のように、Pluto セルが削除されるとすぐに基盤となるタスクが中断されます。
