```
repair!(buf::AbstractThreadsBuffer)
```

ThreadsBuffer `buf` を修復し、すべてのバッファを解放してプールをリセットします。

この関数は、バッファが正しく解放されなかった場合にスレッドループの後に使用する必要があります。
